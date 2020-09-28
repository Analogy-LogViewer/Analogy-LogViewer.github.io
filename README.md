Hi all,
A lot has changed from my last year post of presenting Analogy Log Viewer.
The application has grown from few repositories to more than 41 repositories.
The new version (currently V4.2.8) has new features that I would like to highlight here.
Offline Data Providers
First, I have added support for many known logging frameworks and formats like: Serilog, NLog, Json Parser, XML Parser, Regular Expression Parser,
Windows Event log Parser(Supports real time Event listening) and many special parsers such as Visual Studio crash log parser, Whatsapp Parser.
What's really new: Real Time Streaming:
During the last year I worked on adding Real time log streaming. Viewing logs in real time is very important to debugging and analyzing issues. For this purpose I have added gRPC support and created Windows Service that receives all logs and shows them in real time in the application.
Real time log streaming form different platforms/cumputersThe idea is to stream logs from many executables/computers and view them together in one single window with all standard features like filtering, bookmarking, exporting and saving. The Windows service also has a flag to save all the log to a log file to view later on again if needed.
After creating the windows service I have added many streaming clients to Analogy Log Server: I created NLog Target and Serilog Sink
clients that by configuring the NLOG.config and appSettings.json files you can start sending your logs the the Server/Viewer.
I have also create AspNetCore extension that you can plug directly into your .Net Core App.
One of the nice things about gRPC is that it has many supported languages beside C#. With this I was able to create Python gRPC client and plan to add more languages later on.
Tools
Beside the standard filtering are viewing logs I have added many analyzing tools: I added many types of charts and graphs like the following:
Pie chartsTimeline chartsand even newest tool - Json Visualizer that can create tree like view of any Json object (including embedded Json in your log message):
Json VisualizerConclusion
I have created the log viewer at my old place, Philips Healthcare, during my off hours due to the fact that we didn't have modern, friendly Log viewer and no one took the initiative to create a replacement log viewer to the existing one.
I can say with confident that my log viewer saved a lot of wasted time and frustration for the developers. We used it daily with many improvements along the way.
I decided to make it open source so other developers can have modern log viewer that support common formats in the community.
The application has public API to create custom log providers so if you have logs that are not common you can create your own parser and incorporate it in the application.
Feel free to comment here or at Github or event create your own data providers for Analogy Log Viewer.
Happy coding :)
Lior Banai @ Github