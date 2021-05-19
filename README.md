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
    [150 50 90 30]);

%Second joint angle label
uicontrol("Style","text","String","Second Joint Angle","Position", ...
    [350 50 90 30]);

%Add run button 
Button = uicontrol("Style","pushbutton","string","run","position", ...
    [250 50 100 30], "callback", @PlotGUI);

%Add slider for first joint
Slider1 = uicontrol("Style","slider","Min",0,"Max",180,"Position", ...
    [250 50 200 30]);

%Add slider for the second joint
Slider2 = uicontrol("Style","slider","Min",0,"Max",120,"Position", ...
    [350 50 200 30]);
