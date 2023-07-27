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
dt = +γI
