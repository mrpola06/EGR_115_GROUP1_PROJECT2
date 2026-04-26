%% Group Project 2 - Orbital Distance Calculator 
% Group Members - Odin Ebert, Griffin Heil, Hunter Logan, Maccabee Meinig, Aiden Murphrey, Isabel Scalia 

clear; clc; close all;

% Define Constants 
G = 6.67430e-11; 

%% Inputs: Mass of the planet, Radius of the Planet, Velocity or Distance Choice, Distance Value, Velocity Value

disp('sun=1, mercury=2, venus=3, mars=4, jupiter=5, saturn=6, uranus=7,Neptune=8,Earth=9')
planet = input('Enter 0-9 for a preset planet (0 for custom): ');

if planet == 0
    % Custom planet
    mass = input('Enter planet mass (kg): ');
    if isempty(mass) || ~isnumeric(mass) || ~isscalar(mass) || mass <= 0
        error('Mass must be a positive numeric scalar (kg).');
    end

    planet_radius = input('Enter planet radius (m): ');
    if isempty(planet_radius) || ~isnumeric(planet_radius) || ...
       ~isscalar(planet_radius) || planet_radius <= 0
        error('Planet radius must be a positive numeric scalar (m).');
    end

elseif planet == 1
    mass = 1.9891e30;        % sun
    planet_radius = 6.957e8;

elseif planet == 2
    mass = 3.30e23;        % Mercury
    planet_radius = 2.44e6;

elseif planet == 3
    mass = 4.87e24;        % Venus
    planet_radius = 6.05e6;

elseif planet == 4
    mass = 6.42e23;        % Mars
    planet_radius = 3.39e6;

elseif planet == 5
    mass = 1.90e27;        % Jupiter
    planet_radius = 6.99e7;

elseif planet == 6
    mass = 5.68e26;        % Saturn
    planet_radius = 5.82e7;

elseif planet == 7
    mass = 8.68e25;        % Uranus
    planet_radius = 2.54e7;

elseif planet == 8
    mass = 1.02e26;        % Neptune
    planet_radius = 2.46e7;

elseif planet == 9
    mass = 5.97219e24;        % Earth
    planet_radius = 6371000;

else
    error('Invalid selection. Enter an integer from 0 to 9.');
end

sel = menu('Provide which quantity?', 'Orbital Radius [m]', 'Velocity [m/s]'); 
if sel == 0 
    error('No selection made.'); 
end 

if sel == 1 
    r = input('Enter orbital distance r from planet surface (m): '); 
    r = r + planet_radius;
    if isempty(r) || ~isnumeric(r) || ~isscalar(r) || r <= planet_radius 
        error('Orbital distance must be a numeric scalar greater than zero.'); 
    end 
else 
    v = input('Enter velocity v (m/s): '); 
    if isempty(v) || ~isnumeric(v) || ~isscalar(v) 
        error('Velocity must be a numeric scalar (m/s).'); 
    end 
end 
%% Physics Connection
if sel == 1 
    grav = grav_accel(mass, r, G); 
    T = orbital_period(mass, r, G); 
    v = sqrt(G*mass/r); 
    choice = 'r'; 
else 
    r = ideal_dist(mass, v, G); 
    grav = grav_accel(mass, r, G); 
    T = orbital_period(mass, r, G); 
    if r <= planet_radius 
        error('Computed orbit is below planet radius (not a valid orbit).'); 
    end 
    choice = 'v'; 
end 

% Display results
fprintf('mass: %.2e kg\n', mass)
fprintf('planet_radius: %.2e m\n', planet_radius)
fprintf('choice: %s, r: %.2e m\n', choice, r)
fprintf('v: %.2e m/s\n', v)
fprintf('grav: %.2e m/s^2\n', grav)
fprintf('T: %.2e s\n', T)

%% Loops

if sel == 1 
    n = 200; 
    r_vec = linspace(r, 10*r, n); 
    v_vec = zeros(1,n); 
    for i = 1:n 
        v_vec(i) = sqrt(G*mass./r_vec(i)); 
    end 
    data.r = r_vec; 
    data.v = v_vec; 
end 

if sel == 2 
    n = 50; 
    v_vec = linspace(v*0.95, v*1.05, n); 
    r_vec = zeros(1,n); 
    for i = 1:n 
        r_vec(i) = G*mass./(v_vec(i).^2); 
    end 
    data.r = r_vec; 
    data.v = v_vec; 
end 
%% 3D Plotting with Animation

figure('Color', 'w'); 

t_layout = tiledlayout(1,1,'Padding','tight','TileSpacing','tight');
nexttile;

title(t_layout, 'Satellite Orbit Simulation', 'FontSize', 14, 'FontWeight', 'bold')
subtitle(t_layout, 'Real-time Position Tracking')

% PlottingPlanet
R_planet = planet_radius; 
[xs,ys,zs] = sphere(50); 
surf(R_planet*xs, R_planet*ys, R_planet*zs,... 
    'FaceColor',[0.2 0.6 1],... 
    'EdgeColor','none') 
hold on 

% Generate Orbit Points
t_pts = linspace(0, 2*pi, 300); 
x_vals = x_orbit(t_pts, r);
y_vals = y_orbit(t_pts, r);
z_vals = z_orbit(t_pts);

%Plot Static Orbit Path
plot3(x_vals, y_vals, z_vals, 'r--', 'LineWidth', 1) 

% Initialize Satellite Handle

hSat = scatter3(x_vals(1), y_vals(1), z_vals(1), 100, 'filled', 'y', ...
                'MarkerEdgeColor', 'k'); 

%Axis and View Controls
axis tight           
axis equal           
axis vis3d           
grid on 
xlabel('x (m)'); ylabel('y (m)'); zlabel('z (m)') 

% Lighting for 3D effect
camlight 
lighting gouraud 
material dull 
view([50 40])

% Animation Loop

while true
    for k = 1:length(t_pts)
        hSat.XData = x_vals(k);
        hSat.YData = y_vals(k);
        hSat.ZData = z_vals(k);
        drawnow
    end
end


%% Functions 

function g = grav_accel(mass, dist, G) 
    g = (G * mass)/(dist ^ 2); 
end 

function dist = ideal_dist(mass, vel, G) 
    dist = (G * mass)/(vel ^ 2); 
end 

function T = orbital_period(mass, dist, G) 
    T = 2*pi*sqrt((dist^3)/(G*mass)); 
end

function x_orb = x_orbit(t, r_val)
    x_orb = r_val * cos(t);
end

function y_orb = y_orbit(t, r_val)
    y_orb = r_val * sin(t);
end

function z_orb = z_orbit(t)
    z_orb = zeros(size(t));
end
