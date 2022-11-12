{0: (1.0, 1.0, 0.5),
 1: (0.98, 0.995, 0.499),
 2: (0.96, 0.99, 0.498),
etc


# imports
import matplotlib.colors as colors
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

# vars
dlen = 400
dscalar = 0.04
rscalar = 0.02
gscalar = 0.005
bscalar = 0.001

# data and colors
dd = dict.fromkeys(range(dlen))
cd = dict.fromkeys(range(dlen))
for i in range(dlen):
    # data
    d = [1 + (i * dscalar), 2, 3 - (i * dscalar)]
    dd[i] = d
    # colors
    r = round(1 - (rscalar * i), 3)
    g = round(1 - (gscalar * i), 3)
    b = round(0.5 - (bscalar * i), 3)
    color = (r, g, b)
    cd[i] = color
df = pd.DataFrame(data=dd)
color_dict = cd

# plotting
df.plot(legend=True, cmap=colors.ListedColormap(list(color_dict.values())))
plt.show()

# alternative: color dict using get_cmap
cdget = plt.get_cmap("turbo")(np.linspace(0, 1, dlen))
color_dict = cdget
df.plot(legend=True, cmap=colors.ListedColormap(color_dict))
plt.show()
