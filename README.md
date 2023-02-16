# ChemE 375 Final Exam (Wi2020)

The final exam consists of problems to be solved using Excel (Problems 1-3), Python (Problems 4-5) and Aspen (Problem 6). You should submit accompanying program files (Excel, Python, and Aspen) with your solutions. You are not required to submit Aspen files for P6, but can instead submit an Excel spreadsheet with the data copied from your simulation. The exam can be completed outside of class. You will have 24 hours to complete the exam from Wednesday, March 18 11:00 AM to Thursday, March 19 11:00 AM (but the exam should by no means require 24 hours to complete!).

You may use all course materials to complete the exam, including recorded lectures, homeworks, and notes you may have taken. You are also free to use Google and Stack Overflow for help as well. The exam is essentially open-everything **except** open neighbor. Do **not** communicate with classmates or others, whether by phone, email, social media, or in-person, or otherwise. You will be required to initial an honor statement at the end of the exam certifying you have abided by these rules.

**Please be very careful in annotating your work**. In Jupyter notebooks, you can provide commentary or give written responses to questions in Markdown cells. You can also comment directly in your code using Python comments (starting lines with a # turns it into a comment). For Excel or Aspen problems, you can use text boxes. You can also directly write in the `README.md` file. **The more comments you provide, the easier it will be for me to follow your work.*

**Make sure to type your name at the bottom of the README file before submitting, signifying that you abided by the rules of the exam.**


# Excel

## Problem 1

You are trying to determine the reaction kinetics of a novel reaction in the lab that converts A and B into C. You have collected the following data on the reaction rate from the lab while varying the initial concentrations of the reactants A and B:

| Experiment | r (M/s)      | A (M)   | B (M)   |
| ---------- | ------------ | ------- | ------- |
| 1          | 4.94 x 10^-6 | 0.1     | 0.1     |
| 2          | 1.14 x 10^-5 | 0.1     | 0.5     |
| 3          | 1.62 x 10^-5 | 0.1     | 1.0     |
| 4          | 2.72 x 10^-5 | 0.5     | 0.1     |
| 5          | 6.09 x 10^-4 | 0.5     | 0.5     |
| 6          | 8.85 x 10^-4 | 0.5     | 1.0     |
| 7          | 1.60 x 10^-3 | 1.0     | 0.1     |
| 8          | 3.45 x 10^-3 | 1.0     | 0.5     |
| 9          | 5.02 x 10^-3 | 1.0     | 1.0     |

where M are molar units moles/liter. You are modeling the reaction kinetics using a relationship of the following form:

<a href="https://www.codecogs.com/eqnedit.php?latex=r=kA^{a}B^{b}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?r=kA^{a}B^{b}" title="r=kA^{a}B^{b}" /></a>

1. Using the above reaction kinetics data, use Solver in Excel to calculate k, a, and b. Report the sum of squared errors. Recall that the sum of squared errors measures the difference between an actual value and the value calculated using your model, in this case, using a log scale:

<a href="https://www.codecogs.com/eqnedit.php?latex=SSE&space;=&space;\sum_{i}{(\ln{r_i}&space;-&space;\ln{r_{model,i}})^2}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?SSE&space;=&space;\sum_{i}{(\ln{r_i}&space;-&space;\ln{r_{model,i}})^2}" title="SSE = \sum_{i}{(\ln{r_i} - \ln{r_{model,i}})^2}" /></a>

2. You know that experiments aren't perfect, and that each experimental result has some uncertainty associated with it that could give you inaccurate results. In order to quantify the impact of this uncertainty, repeat the procedure in (1) nine times by **excluding one datapoint from the analysis one at a time.** For instance, in case one, ignore the data from experiment 1, and calculate k, and, and b based only on experiments 2-9. Report the minimum and maximum values of each parameter you found, as well as the sum of squared errors for each calculation.

3. You suspect that there was a transcription error in your lab notebook for one of the experiment runs, but you aren't sure which one it was. Based off your results from part (2), which experiment has a transcription error? *Hint: Look at the relative size of the sum of squared errors*.

4. After identifying the run that was an error, you exclude it from your analysis. Repeat (2) after excluding the run in error. How does the range of your minimum and maximum values for each parameter change? How do your sum of squared errors change?

## Problem 2

You are trying to optimize the following reaction in the lab:

<a href="https://www.codecogs.com/eqnedit.php?latex=A&space;&plus;&space;2B&space;\rightarrow&space;C&space;\\&space;r_1&space;=&space;k_1[A][B]^2,&space;\&space;\&space;\&space;k_1&space;=&space;0.050&space;M^{-2}s^{-1}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?A&space;&plus;&space;2B&space;\rightarrow&space;C&space;\\&space;r_1&space;=&space;k_1[A][B]^2,&space;\&space;\&space;\&space;k_1&space;=&space;0.050&space;M^{-2}min^{-1}" title="A + 2B \rightarrow C \\ r_1 = k_1[A][B]^2, \ \ \ k_1 = 0.050 M^{-2}min^{-1}" /></a>

Unfortunately, there are two side reactions that compete with the available reactants:

<a href="https://www.codecogs.com/eqnedit.php?latex=2A&space;\rightarrow&space;D&space;\\&space;r_1&space;=&space;k_2[A]^2,&space;\&space;\&space;\&space;k_2&space;=&space;0.010&space;M^{-1}s^{-1}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?2A&space;\rightarrow&space;D&space;\\&space;r_1&space;=&space;k_2[A]^2,&space;\&space;\&space;\&space;k_2&space;=&space;0.010&space;M^{-1}min^{-1}" title="2A \rightarrow D \\ r_2 = k_2[A]^2, \ \ \ k_2 = 0.010 M^{-1}min^{-1}" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=C&space;&plus;&space;B&space;\rightarrow&space;E&space;\\&space;r_3&space;=&space;k_3[C][B],&space;\&space;\&space;\&space;k_3&space;=&space;0.0012&space;M^{-1}s^{-1}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?C&space;&plus;&space;B&space;\rightarrow&space;E&space;\\&space;r_3&space;=&space;k_3[C][B],&space;\&space;\&space;\&space;k_3&space;=&space;0.0012&space;M^{-1}min^{-1}" title="C + B \rightarrow E \\ r_3 = k_3[C][B], \ \ \ k_3 = 0.0012 M^{-1}min^{-1}" /></a>

Your goal is to tune the initial concentrations of A and B (there is no C, D, or E initially) to maximize the final concentration of C. For the purposes of your calculations, you quench the reaction after 10 minutes so it no longer reacts.

1. Using a finite difference method, calculate the concentration profiles of A, B, C, D, and E over time if the initial reactant concentrations are A = 2M and B = 2M. Use a time interval of 0.1 min for your calculations. Also report the final selectivities of C with respect to D and E. Plot the concentration profiles of each compound on the same graph.

2. Use solver to find the initial concentrations of A and B that will give you the highest concentration of C. The highest concentrations of A and B that can be achieved in solution are 5 M and 5 M, respectively (use these as constraints within solver). Also report the final selectivities of C with respect to D and E. Plot the concentration profiles of A, B, C, D, and E given this set of initial conditions.

3. Because the product E is toxic, you have to add an additional constraint: E can only achieve a maximum concentration of 0.1 M. Use solver to maximize C give the new constraint. Similar to (1) and (2), report the selectivities and plot the concentration profiles.

4. While D isn't toxic, you want to minimize its production because you have a way to recycle unreacted A and B. You want to try to maximize C while keeping the highest concentration of D below 0.15 M, while still maintaining E below 0.1 M. Use solver to maximize C given the new additional constraint. Report the selectivities and plot the concentration profiles.

Make sure that all plots are well-formatted, and make sure that the range of both x and y are the same in all plots.

## Problem 3

Many reactions used in industry to produce chemical products do not have high conversion rates, often lower than 75%. In order to economize the use of raw materials, it is a common practice to use a recycle stream: unreacted raw materials are mixed with the stock raw materials and re-sent through the reactor.

In the problem given below, the following reaction is being studied:

<a href="https://www.codecogs.com/eqnedit.php?latex=A&plus;B\rightarrow&space;C" target="_blank"><img src="https://latex.codecogs.com/gif.latex?A&plus;B\rightarrow&space;C" title="A+B\rightarrow C" /></a>

Reactant stream 1 composed of 12 kmol/h A and 10 kmol/h B is mixed with the recycle stream 7 before being sent to the reactor. The reactor achieves 75% conversion of B. The effluent from the reactor is sent to a separator that can achieve a perfect separation of A and B from C (100% A and B ends up in stream 5), while 95% of product C is recovered in stream 4.

![](https://github.com/uw-cheme375/uw-cheme375.github.io/raw/master/images/Final_P3a.jpg)

You have direct control over how much of Stream 5 you send back into the reactor in Stream 7 (the recycle stream) and how much you remove as a product or waste stream in Stream 6 (the purge stream). You can quantify this as the split fraction, the ratio of the flow rate of Stream 7 to Stream 5. You are analyzing how the split fraction of the recycle stream impacts the economics of the process: how does overall conversion of B change with the split fraction? How does the flow rate of the recycle stream change with the split fraction?

Note that the given problem is non-linear: the recycle stream is both an input AND an output, so you can't solve the problem directly. In order to solve, we will break or "tear" the recycle stream so our process now looks like this:

![](https://github.com/uw-cheme375/uw-cheme375.github.io/raw/master/images/Final_P3b.jpg)

In order to solve the problem, make an initial guess of the composition of the recycle stream (stream 7a), and solve for the output streams 4, 6, and 7. Use solver to find the correct composition of stream 7a by minimizing the difference between the compositions of 7 and 7a.

As a final output, generate two separate graphs: (1) the overall conversion of B as a function of the split fraction and (2) the total flow rate of the recycle stream as a function of the split fraction. At a minimum, plot both graphs using 10% intervals of the split fraction up to a split fraction of 99.9%.

Based on these results, why do you think we don't recycle all or almost all of the unreacted reactants to achieve the highest conversion?

# Python

## Problem 4

In class, we created a class object to store and plot VLE data. We used the following code:

    class VLE():
      def __init__(self, T, xi, yi, P, Psat1, Psat2):
          self.T = T
          self.P = P
          self.xi = xi
          self.yi = yi
          self.Psat1 = Psat1
          self.Psat2 = Psat2

      def plot_vle(self):

          fig, ax = plt.subplots()

          ax.scatter(self.xi, self.T, color='k')
          ax.scatter(self.yi, self.T, color='k')

Add the following functions to this class that perform the following tasks:

* Psat_calc(self, T=70, comp=1): Performs a saturation pressure calculation at the input temperature (T) for the specified component.
* activities(self): Calculates the activity coefficients for both component 1 and 2.
* actplot(self): Plots the activity coefficients as a function of the molar concentration of component 1 in the liquid phase

Demonstrate that your code works using two different two-phase systems e.g. ethanol-methanol or acetone-water. You may look up the Antoine coefficients and vapor-liquid equilibrium data from reliable sources such as the [Dortmund Data Bank](http://www.ddbst.com/en/EED/VLE/VLE%20Ethanol%3BMethanol.php). As a reminder, you can calculate the activity coefficients using the following equations:

<a href="https://www.codecogs.com/eqnedit.php?latex=\gamma_1&space;=&space;\frac{y_1p}{x_1p_1^s},&space;\text{and&space;}&space;\gamma_2&space;=&space;\frac{(1-y_1)p}{(1-x_1)p_2^s}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\gamma_1&space;=&space;\frac{y_1p}{x_1p_1^s},&space;\text{and&space;}&space;\gamma_2&space;=&space;\frac{(1-y_1)p}{(1-x_1)p_2^s}" title="\gamma_1 = \frac{y_1p}{x_1p_1^s}, \text{and } \gamma_2 = \frac{(1-y_1)p}{(1-x_1)p_2^s}" /></a>


## Problem 5

Load the meteorite landing dataset available through [NASA](https://data.nasa.gov/Space-Science/Meteorite-Landings/gh4g-9sfh) into a Pandas dataframe.

1. Use the function that gives an overview of some basic statistics of the data. What is the mean size of the meteorites? The median size of the meteorites?
2. Use some of the functionality of pandas dataframes to find the five largest meteorites ever to strike earth. How big were they? Were they found after they fell, or was their fall witnessed (see the 'fall' column)?
3. Create a new column in your pandas dataframe called 'logmass' that represents the log of the mass in grams. Create a histogram plot of the log masses.
4. Create a map of the fallen meteorites by plotting the 'reclat' and 'reclog' columns (make sure to use the 'scatter' function, not the 'plot function'). Make the plot more readable by specifying the transparency of the markers by changing the 'alpha' parameter to an appropriate value. Code in the size of the meteorites by scaling marker size with meteorite size (e.g. bigger markers mean bigger meteorites, smaller markers mean smaller meteorites). In order for this to work, you will have to use either the 'mass (g)' data, the 'logmass' data, or some other alternate scaling of the size data. If your chosen scaling of size data makes points that are too small to read, or too large to be useful, choose an alternate scaling of the size data e.g. include a some sort of threshold. It may be useful to look at the meteorite size histogram prior to constructing your scaling. In the end, you should be able to see both large and small markers. Additionally, represent the found status of the meteorites ('fell' or 'found') as the color of the markers.

**Hint**: If you've plotted correctly, the map should resemble a world map of the continents. Make sure to adjust the figure size and orientation accordingly.

**Hint**: There may be one or two datapoints with latitude and longitude coordinates that don't make sense. You should remove these from the dataset before plotting.


# Aspen

## Problem 6

Water and formic acid form an azeotrope making this separation particularly difficult. Read up on azeotropes [here](https://en.wikipedia.org/wiki/Azeotrope) if they are unfamiliar.

A common method to break azeotropes to perform a complete separation is to use two distillation columns operating at different pressures, also known as a pressure swing. This problem explores this method.

1. In Aspen, create a Txy diagram for the water-formic acid mixture at 1 bar using the following thermodynamics packages: IDEAL, SRK, and UNIQUAC. Which packages are able to capture the azeotropic behavior of the mixture? Which is the most accurate?
2. You are attempting to construct a sequence of distillations to get pure water and pure formic acid. Given a feed concentration of x=0.2 water, what would be the highest concentration of water I could achieve in my bottoms product? What would the temperatures of my distillate and bottoms products be?
3. Make similar Txy diagrams at 4 bar and 0.6 bar. Using these results, devise a separation strategy to achieve pure water and pure formic acid. Be sure to report the concentrations of all input and output streams in each column and the pressures at which each column operates.

Please either (a) provide Aspen files in the repo as well as embedded image files of each Txy diagram below or (b) Excel files with data copied from Aspen and Txy plots in Aspen or Excel.

## Honor Statement

I, the undersigned, acknowledge that I did not communicate with classmates, professors, or other individuals living or dead in any way about the exam material while taking the exam.
