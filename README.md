# reelgraph
Auto-generated graphical representation of video files

Question:

Can we automatically create a timeline or "plot" of a movie or TV series, by using CV to identify unique scenes and characters, connecting them in a graph representation, and then build a plot like the following: https://mankindunplugged.com/wp-content/uploads/2015/12/star-wars-infographic-episode-1-2-3.jpg

Motivation:

Video content is getting more and more popular. Streaming services put out a huge amount of new content through platforms like Netflix, HBO, Youtube - yet much of this content is not directly observable at a glance. Can we use methods from AI/ML to start structuring some of this video content in a way thats more instantly usable, searchable, useful, or memorable, without having to pour over hours of content, scrubbing timelines back and forth? Can this data be presented in a user interface thats more intuitive and has greater utility?

Some use cases:

1) A user wants to get caught up on the plot of a streaming series on Netflix. They want to know what happened in the past two seasons, but reading thru long text summarys is slow, painful, and doesnt help with recall of the actual story. Instead, the user can bring up the reelgraph page for this show, which automacitally generates a visual timeline of the show, and includes icons for major scenes, events and characters that can be clicked on for further info.

2) An educational video series covers a scientific topic in depth, such as chemistry. This includes hours and hours of lectures on various subjects. The user is interested in solving a specific chemistry problem that potentially links together many of the in depth topics, however, these topics are spread across many different hour long lectures, and are difficult to find, extract and connect in a coherent way. Instead of doing this manually, the user goes to the reelgraph page, which shows the topics listed out in a timeline across all the videos, as well as links between connected topics. By searching the graph for their topic, they can instantly see the other connected topics, and go straight to the content that is specifically relavent to the problem they are trying to solve. This saves the user multiple hours in search time, and potentially reveals connections they would not have been aware of otherwise.

Open questions to answer:

-what is the simplest version of this problem?
-what is the most concrete use case we are interested in tackling first?
-what will our first end product be? script? image? webapp?
-can we break up the problem in a modular way and work in parallel?
-what are the major components of the problem?

Potential major components/pipeline:

1-data ingestion. take in the video file or stream, and send each frame to a processor with a timestamp and frame number (do we use keyrfames? how do we do this for various sources?)
2- frame processing - look at each frame, and, using CV, ID major components of the frame (scene, people, characters, objects, etc...)
3 - frame context - look for continuity of major components in adjacent frames - can we ID scene changes? can we ID that it is the same scene from a different vantage point? Can we ID characters from different vantage points?
4 - graph database - create a graph representation that holds the major components ID'ed across frames and scenes as nodes, and automatically connects these nodes with labeled relationships.
5 - audio - transcribe audio, and pin to various scenes. ID major topics, if possible, and add to graph as node.
6 - visualization - take the build up graph of nodes and relationships, and somehow translate that into a visual interface.
