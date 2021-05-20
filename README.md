# GUI---Assignment-1

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

%Retrieves value from the slider using parameters
Param = get(Slider1,"value");

%Put value retrieved from slider onto the GUI
uicontol("Style","text","string", num2str(Param), "position",...
    [460 55 60 20]);
    
%Plotting on the graph
x = linspace(0, 10, 1000);
k = Param;
y = sin(k*x);
plot(x,y);

end
