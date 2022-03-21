# bellcurve

import plotly.figure_factory as ff
import statistics
import random
import pandas as pd
import csv
import plotly.graph_objects as go

df = pd.read_csv("data.csv")
data = df["temp"].tolist()
population_mean = statistics.mean(data)
std_deviaton = statistics.stdev(data)
print("population mean :- ", population_mean)
print("standard deviation :- ", std_deviaton)
fig = ff.create_distplot([data], ["temp"], show_hist = False)
fig.show()

def show_fig(mean_list):
    df = mean_list
    fig = ff.create_distplot([data], ["temp"], show_hist = False)
    fig.add_trace(go.Scatter(x=[mean, mean], y=[0,1], mode = "lines", name = "Mean"))
    fig.show()

dataset = []
for i in range(0,100):
    random_index = random.randint(0, len(data))
    value = data[random_index]
    dataset.append(value)
mean = statistics.mean(dataset)
std_deviaton = statistics.stdev(dataset)

print("Mean Of Sample = ", mean)
print("standard deviation of Sample", std_deviaton)

def random_set_of_mean(counter):
    dataset = []
    for i in range(0,counter):
        random_index = random.randint(0,len(data))
        value = data[random_index]
        dataset.append(value)
    mean = statistics.mean(dataset)
    return mean

def show_fig(mean_list):
    df = mean_list
    fig = ff.create_distoplot([df], ["temp"], show_hist = False)
    fig.show()

def setup():
    mean_list = []
    for i in range(0, 1000):
        set_of_means = random_set_of_mean(100)
        mean_list.append(set_of_means)
    show_fig(mean_list)

setup()
