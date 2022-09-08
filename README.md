# model reconstruction based on takens approach
Taking a time series s one can create a n dimensional system by creating n shifted series from the original series:

'''python
s_0 = [...]  # original series
s_1 = np.roll(s_0, shift_1)
s_2 = np.roll(s_0, shift_2)
...
s_n = np.roll(s_0, shift_n)

system = [s_0, ..., s_n]
'''

According to Takens for a successful reconstruction one must choose the dimensions and shift sucht, that the trajectory in the phasespace must not hit itself.
Such, for the shifts we create the criteria that for each point of the trajectory any other point must be as far away as possible. We can calculate the shifts by maximizing the mean distance for every shift. This results in an n-1 dimensional minimizing problem. To solve it, one can use simulating annealing potential dynamics. Easy — or is it?