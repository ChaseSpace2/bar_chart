# bar_chart
Multi bar chart
import csv
import numpy as np
from matplotlib import pyplot as plt

# Mach hrs for December.
filename = 'capacity.csv'
with open(filename) as f:
    reader = csv.reader(f)
    header_row = next(reader)

    Machs, ActRTs = [], []
    for row in reader:
        Mach = (row[6])
        Machs.append(Mach)
                        
        ActRT = int(float(row[23]))
        ActRTs.append(ActRT)
        
x = [200, 300, 400, 200, 200, 300, 100, 400, 300, 200, 100, 200, 300, 500, 200]

# Plot data.
fig = plt.figure(dpi=128, figsize=(20,12))
bar_width = .15
plt.bar(Machs, ActRTs, width=bar_width, color='blue')
plt.bar(Machs + bar_width, x, width=bar_width, color='green')

# Format plot.
plt.title("Run hours by Machine", fontsize=24)
plt.xlabel("Machines", fontsize=16)
plt.ylabel("ActRTs", fontsize=24)
plt.tick_params(axis='both', which='major', labelsize=16)

plt.show()
