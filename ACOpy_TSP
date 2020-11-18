import tsplib95
import acopy
import matplotlib.pyplot as plt
import pandas as pd

solver = acopy.Solver(rho=.003, q=0.2)
colony = acopy.Colony(alpha=1, beta=3)
problem = tsplib95.load('berlin52.tsp')
G = problem.get_graph()
tour = solver.solve(G, colony, limit=450)

print(tour.cost)
print(tour.get_id())
print(tour.nodes)
print(tour.path)

df = pd.read_csv("berlin52.csv")
X = df.iloc[:,0:1].values
Y = df.iloc[:,1:2].values

fig = plt.figure(figsize=(7, 5))
plt.scatter(X,Y,15,c="red")
plt.plot(X,Y,3,c="grey")
plt.plot([X[len(X)-1][0],X[0][0]], [Y[len(Y)-1][0],Y[0][0]],"black")
plt.xlabel("X Axis")
plt.ylabel("Y Axis")
plt.show()

X_new = []
Y_new = []
for i in tour.path:
    X_new.append(X[i[0]-1])
    Y_new.append(Y[i[1]-1])

plt.scatter(X_new,Y_new, c = "orange")
plt.plot(X_new,Y_new, c = "purple")
plt.plot([X_new[len(X_new)-1][0],X_new[0][0]], [Y_new[len(Y_new)-1][0],Y_new[0][0]],"black")
plt.xlabel("X Axis")
plt.ylabel("Y Axis")
plt.show()
