# MACM316_final_assignment
% 1 A&B
t = 180; 

N = 5000000;
Ra = 2.5;
gamma = 1/10;
alpha = 1/5;
beta = Ra *gamma;

S = zeros(t,1);
I = zeros(t,1);
R = zeros(t,1);
E = zeros(t,1);

R(1) = 0;
I(1) = 40;
S(1) = N - I(1) - E(1) - R(1);
E(1) = 20 * I(1); 
for i = 2:t
    
    S(i) = S(i-1) - beta*I(i-1)*S(i-1)/N; 
    E(i) = E(i-1) + beta*I(i-1)*S(i-1)/N - alpha*E(i-1);
    I(i) = I(i-1) + alpha*E(i-1) - gamma*I(i-1);
    R(i) = R(i-1) + gamma*I(i-1);
   
    
end

plot(1:t,S,'LineWidth',2)
hold on
plot(1:t,E,'LineWidth',2)
hold on
plot(1:t,I,'LineWidth',2)
hold on
plot(1:t,R,'LineWidth',2)
grid on

legend("Susceptible", "Exposed", "Infected","Removed")
xlabel("Time")
ylabel("Population")

%1C
t = 180; 

N = 5000000;
Ra = 2.5;
gamma = 1/10;
alpha = 1/5;
beta = Ra *gamma;

S = zeros(t,1);
I = zeros(t,1);
R = zeros(t,1);
E = zeros(t,1);
CASES = zeros(t,1);

R(1) = 0;
I(1) = 40;
S(1) = N - I(1) - E(1) - R(1);
E(1) = 20 * I(1); 

for i = 2:t
    S(i) = S(i-1) - beta*I(i-1)*S(i-1)/N; 
    E(i) = E(i-1) + beta*I(i-1)*S(i-1)/N - alpha*E(i-1);
    I(i) = I(i-1) + alpha*E(i-1) - gamma*I(i-1);
    R(i) = R(i-1) + gamma*I(i-1);
    CASES(i) = alpha*E(i-1);
end

plot(1:t,CASES,'LineWidth',2)





