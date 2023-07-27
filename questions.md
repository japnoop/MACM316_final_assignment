A simplified COVID-19 model
The so-called SEIR model is a standard way to model the spread of infectious diseases. It is
an example of a compartmental model. We will look at this model in its most basic form, and
solve it numerically for various parameters.
The population of N individuals is assigned to different compartments, and individuals can
move between compartments. The SEIR model uses four compartments, S, E, I, R, representing segments of the population, so S + E + I + R = N (a simplification, meaning the total
population is constant, with some leeway in interpreting the term “total population”).
S. Susceptible individuals. Those are healthy, and not immune individuals who may become infected upon contact with an infected individual.
E. Exposed individuals. These are individuals who have been infected, but because of the
incubation period of the virus are not yet infectious themselves. They will transition to
the infected group;
I. Infected individuals. These are individuals who have been infected, and can pass on the
infection to susceptible individuals.
R. Removed individuals. (In an optimistic scenario referred to as recovered individuals.)
These include people who have recovered and are now immune, and people who have
deceased.
Note that for Covid-19, it is still not clear yet whether recovered people are immune to the
virus and its variants, and if so, by how much and for how long. This simplified model assumes
they become immune to the virus and its variants. Interactions between people in compartments are proportional to the number of people in each compartment. Transfers from one
compartment to another that do not involve interactions are assumed to occur proportional to
the number of people in one compartment, corresponding to linear terms. The equations are
as follows (the variable t is time, say measured in days):
dS
dt = −βI S
N
susceptibles become exposed due to interaction with I, contact rate of β
dE
dt = +βI S
N
− αE incoming S minus exposed moving to I, α = 1/incubation period
dI
dt = +αE − γI incoming exposed - “removed”, γ = 1/infectious period
dR
dt = +γI<br>

1. Implementation.<br>
a). Write Matlab code to solve the SEIR equation. You may use the the code SIR.m to simulate the process or Matlab’s built-in functions, for example ode45 or ode15s, to solve the
SEIR equations numerically.<br>
b). Run the code with the following parameters and initial conditions for t = 180 days and
report a plot of the S, E, I, R curves.
Parameters:
N = 5, 000, 000, roughly the number of individuals in British Columbia.
α = 1/5, incubation period of roughly 5 days.
γ = 1/10, infectious period of 10 days. (The actual period is probably longer, but this value
takes into account that sick people go to hospital or stay home, rather than continuing to circulate among the general population).
R0 = 2.5; you probably have heard about this now infamous parameter R0, the basic reproduction number, which roughly translates to the number of individuals an infected individual
can transmit the virus to on average. For our model we have R0 = β/γ and thus β = R0γ.
(Note that the R in R0 has nothing to do with the compartment of “removed” individuals R.)
Initial conditions:
R(0) = 0, I(0) = 40, E(0) = 20 × I(0), S(0) = N − I(0) − E(0) − R(0).<br>
c). With the same parameters and initial conditions in b) and assuming all infected individuals are reported and recoded (very ideal), the number of incident (new) cases on day t is given
by αE(t − 1). Plot the curve for the number of incident cases.<br>

2. Time-dependent parameters.<br>
a). In reality, some of these parameters will be time dependent – the effect of physical distancing and lockdown or reopening. Let R0 = R0(t), hence, β = β(t) be the time-dependent
parameter. According to the model, β is the contact rate, which can be controlled. If we all
stayed in a remote log cabin by ourselves, β = R0 = 0; if we practice physical distancing and
wear masks when physical distancing is not possible, then R0 might stay below 1; if we hang
out in bars or at large gatherings, then β and R0 will go through the roof – leading to large
numbers of Is, infected and infectious people.
We could model the effect of intervention (e.g. social distancing) with data for R0 as follows
(three scenarios are given):
Days (since outbreak) 1-20 21-70 71-84 85-90 91-110 111-180 after 180
R0 (scenario one) 3.5 2.6 1.9 1.0 0.55 0.55 0.5
R0 (scenario two) 3 2.2 0.7 0.8 1.00 0.90 0.5
R0 (scenario three) 3 2.2 0.9 2.5 3.20 0.85 0.5
Modify the Matlab code in question 1 so they are compatible with the varying R0.<br>
b). Run the modified code with the other parameters unchanged as in question 1. Report
the plots of S, E, I, R curves for the three scenarios. Report the plots of the curves of incident
cases for the three scenarios.<br>

3. Becoming a member of the modeling team for the infectious disease epidemic.<br>
a). Download the case data from BCCDC at http://www.bccdc.ca/Health-Info-Site/
Documents/BCCDC_COVID19_Dashboard_Case_Details.csv. The data include all reported
cases in British Columbia, with information about reported date, health area, sex and age
group of each case. We will only use the reported date. Use the data to create a scatter plot of
number of incident (new) cases in British Columbia on each date. Report the plot.<br>
b). Adjust parameters and initial conditions in the SEIR model with time-dependent R0, so
that the curve of incident cases from the model (e.g. plots in question 2.b) roughly coincides
with the scatter plot of reported cases (see plot in question 3.a). Note that this needs more
than 180 days and you may need to adjust all of the parameters including the time (day)
interval for constant R0, for example, instead of using 1-20 and 21-71, you may need to change
the interval to 1-100 and 101-180. Report the parameters you used and the plot including the
curve of incident cases from the SEIR model and the scattered points of number of reported
incident cases.
