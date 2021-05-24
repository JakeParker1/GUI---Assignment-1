# GUI---Assignment-1

%GUI Operator Control Panel 

%Clear workspace area and command 
clc;
clear;
%Closes any existing graphs 
close all; 
format compact

%Make a large figure 
figure('Position',[0 0 700 500], 'name', 'SimpleGUI', 'NumberTitle', 'off');

%Make subplot to hold plot 
h = subplot('Position', [-3500 3500 0 3000]);

%Title
uicontrol("Style","text","String","Operator Control Panel", "Position", ...
    [250 400 200 30]);

%First joint angle label
uicontrol('style',"text","String","First Joint Angle","Position", ...
    [50 100 100 30]);

%Second joint angle label
uicontrol("Style","text","String","Second Joint Angle","Position", ...
    [200 100 100 30]);

%Third joint angle label
uicontrol("Style","text","String","Third Joint Angle", "Position", ...
    [350 100 100 30]);

%Fourth joint angle label
uicontrol("Style","text","String","Fourth Joint Angle","Position", ...
    [500 100 100 30])

%Add run button 
Button = uicontrol("Style","pushbutton","string","run","position", ...
    [625 100 50 30], "callback", @PlotGUI);

%Add slider for first joint
Slider1 = uicontrol("Style","slider","Min",0,"Max",180,"Position", ...
    [50 50 100 30]);

%Add slider for the second joint
Slider2 = uicontrol("Style","slider","Min",0,"Max",120,"Position", ...
    [200 50 100 30]);

%Add slider for third joint
Slider3 = uicontrol("Style","slider","Min",0,"max",120,"position", ...
    [350 50 100 30]);

%Add slider for fourth joint
Slider4 = uicontrol("Style","slider","Min",0,"Max",120,"position", ...
    [500 50 100 30]);
%Plotting the GUI
function PlotGUI(hObject,eventdata)

%Handle to Slider1
global Slider1;

%Retrieves value from Slider1 using parameters
Param1 = get(Slider1,"value");

%Handle to Slider2
global Slider2;

%Retrieves value from the Slider2 using parameters
Param2 = get(Slider2,"value");

%Handle to Slider3
global Slider3;

%Retrieves value from the Slider3 using parameters
Param3 = get(Slider3,"value");

%Handle to Slider4
global Slider4;

%Retrieves value from the Slider4 using parameters
Param4 = get(Slider4,"value");

%Put value retrieved from Slider1 onto the GUI
uicontol("Style","text","string", num2str(Param1), "position",...
    [50 55 60 20]);

%Put value retrieved from Slider2 onto the GUI
uicontol("Style","text","string", num2str(Param2), "position",...
    [200 55 60 20]);

%Put value retrieved from Slider3 onto the GUI
uicontol("Style","text","string", num2str(Param3), "position",...
    [350 55 60 20]);

%Put value retrieved from Slider4 onto the GUI
uicontol("Style","text","string", num2str(Param4), "position",...
    [500 55 60 20]);
    
%Adding DH table for the joints
base = [1 0 0 0; 0 1 0 0; 0 0 0 1]

%Joint 1 Variables
J1rotz = [cosd(thetaParam1) -sind(thetaParam1) 0 0; sind(thetaParam1)...
    cosd(thetaParam1) 0 0; 0 0 1 0; 0 0 0 1];
J1transz = [1 0 0 0; 0 1 0 0; 0 0 1 dParam1; 0 0 0 1]
J1transx = [1 0 0 aParam1; 0 1 0 0; 0 0 1 0; 0 0 0 1]
J1rotx = [1 0 0 0; 0 cosd(alphaParam1) -sind(alphaParam1) 0; ...
    0 sind(alphaParam1) cosd(alphaParam1) 0; 0 0 0 1]

Joint1 = J1rotz*J1transz*J1rotx*J1transx

%Joint 2 variables
J2rotz = [cosd(thetaParam2) -sind(thetaParam2) 0 0; sind(thetaParam2)...
    cosd(thetaParam2) 0 0; 0 0 1 0; 0 0 0 1];
J2transz = [1 0 0 0; 0 1 0 0; 0 0 1 dParam2; 0 0 0 1]
J2transx = [1 0 0 aParam2; 0 1 0 0; 0 0 1 0; 0 0 0 1]
J2rotx = [1 0 0 0; 0 cosd(alphaParam2) -sind(alphaParam2) 0; ...
    0 sind(alphaParam2) cosd(alphaParam2) 0; 0 0 0 1]

Joint2 = J2rotz*J2transz*J2rotx*J2transx

%Joint 3 variables
J3rotz = [cosd(thetaParam3) -sind(thetaParam3) 0 0; sind(thetaParam3)...
    cosd(thetaParam3) 0 0; 0 0 1 0; 0 0 0 1];
J3transz = [1 0 0 0; 0 1 0 0; 0 0 1 dParam3; 0 0 0 1]
J3transx = [1 0 0 aParam3; 0 1 0 0; 0 0 1 0; 0 0 0 1]
J3rotx = [1 0 0 0; 0 cosd(alphaParam3) -sind(alphaParam3) 0; ...
    0 sind(alphaParam3) cosd(alphaParam3) 0; 0 0 0 1]

Joint3 = J3rotz*J3transz*J3rotx*J3transx

%Joint 4 Variables
J4rotz = [cosd(thetaParam4) -sind(thetaParam4) 0 0; sind(thetaParam4)... 
    cosd(thetaParam4) 0 0;0 0 1 0; 0 0 0 1];
J4transz = [1 0 0 0; 0 1 0 0; 0 0 1 dParam4; 0 0 0 1]
J4transx = [1 0 0 aParam4; 0 1 0 0; 0 0 1 0; 0 0 0 1]
J4rotx = [1 0 0 0; 0 cosd(alphaParam4) -sind(alphaParam4) 0; ...
    0 sind(alphaParam4) cosd(alphaParam4) 0; 0 0 0 1]

Joint4 = J4rotz*J4transz*J4rotx*J4transx

%Plotting on the graph 
x = linspace(0, 10, 1000); 

k1 = Param1; 
y1 = sin(k1x); 
hold on; 

k2 = Param2; 
y2 = sin(k2x); 
hold on; 

k3 = Param3; 
y3 = sin(k3x); 
hold on; 

k4 = Param4; 
y4 = sin(k4x); 
plot(x,y1);
end
