---
layout: post
title: "Data Science Project: Analysis of Poverty Rate"
date: 2018-01-28
author: Calvin Z He
---
After graduating with my bachelor's in 2016, I was stuck in limbo on what to do next with my life.
I had not completed any internships as a student, primarily due to the fact that I most internships took place
throughout the summer, which were occuppied by military training for the Army Reserves (i.e. Basic Leader Course
and Annual Training).  I also had not applied for graduate schools starting in the Fall of 2016 because by the
time applications came around the previous year, I've only worked as an undergraduate research assistant in
Hudson's group for a few months.  I wasn't sure who I'd ask for letters of recommendation or if I even wanted to
go to graduate school.  Along with having to take the GRE and having to decide which schools to apply to and which
research groups in those schools to decide to be interested in, I felt that the whole applications process would
have been very disruptive to my studies.  I just wanted to graduate with a good GPA and possibly some sort of honors.

Cutting to the chase, during the Fall of 2016, I was in the beginning of my post-baccalaureate gap year, and one of the things that I 
had decided
to do was to take a set of online courses on Data Science.  I had first heard about Data Science from an e-mail
sent out to the Physics and Astronomy department's distribution list for undergraduates from an organization called
"Signal Data Science" located in Northern California advertising their pilot boot camp program intended to turn 
graduating STEM students into Data Scientists.  I was curious about the topic of Data Science, but I was not interested
in immediately becoming a Data Scientist as I had my eyes turned towards graduate school, so I decided to look around 
the internet to see if there were other similar educational opportunities in this field.  I later discovered the Microsoft
Data Science Program, taught completely online, on edX and decided to go with that.  I figured, even if I don't become a
Data Scientist in the near future, I might learn some things that would be useful for graduate research.

I was hoping to complete the entire Data Science curriculum by January of next year, but due to graduate school applications, 
me trying to apply for various job positions not realizing it typically takes a year or more to get hired - to include job positions
in the fields of engineering and software development which I was then not qualified for with a mere bachelor's level Physics degree
and a sparse amount of programming experience, volunteering for extra duty in the Army Reserves because of my then extra free time,
deciding to become a part-time math/physics tutor, and my return to video games thanks to moving back home where my gaming rig is
kept, it would take me until the summer of 2017 to complete all of the Data Science courses in the curriculum minus the capstone project.

I attempted the latest capstone project this month, hoping to finally finish up this program.  Actually, I had also decided to take
a Spanish course along with a 1-unit "Math Elements of Quantum Mechanics" course taught by Charles Clark at UMD over the Winter, so most of the time
spent working on the capstone project was during the week during which the Winter session ended and the Spring session began.  Since the
capstone was scheduled for three weeks, I was really compressed for time, and needless to say, I was unable to submit my final report in time.
If only I had a few extra hours, I might have gotten it in and passed the course!  Anyway, here is the (haphazardly written) report itself:
<a href="/documents/analysis_of_poverty_rate_-_data_science_capstone.pdf">Analysis of Poverty Rate</a>.  Seeing that the due date has already past
and that the topic for the capstone project changes each session, it shouldn't be an issue to have this posted.

The project was an interesting one, and can be found at <a href="https://www.datasciencecapstone.org/">https://www.datasciencecapstone.org/</a>.
The topic was about poverty in the United States.  In short, we are given socioeconomic demographic geographic (or however you might put it) data
on some of the counties in the United States (to include their poverty rates, defined in the linked report), and we are supposed to use all that
we have learned in the program to predict the poverty rate of counties in which we do not know the poverty rate of.

I was rather rusty with the
tools, so it took me some time to get things rolling.  I had decided to use Python and the Sci-Kit Learn module to do basically all of the data
exploration and machine learning.  This was because, out of all of the courses I took in the Data Science curriculum, I felt that I gained the most
practical skills from the one on using Python for Data Science.  It was also reviewed by many to be a very difficult course - which I personally didn't think
was that bad, in part thanks to my experience with using Python in Hudson's lab at UCLA as an undergraduate research assistant (I mean, trying to
figure out things like "device wrappers", incorporating asyncronous programming with timed commands, and going into rabbit holes following class
inheritence hierarchies in order to troubleshoot problems associated with an open-source module whose paradigm changes from version to version is
much more frustrating).
Additionally, Python allows everything to done without having to utilize any cloud services.  I'm not a huge fan of web interfaces.  I need my
development environment to be snappy and responsive and not feel like they've been designed for touch screens.

Plain old linear regression
was used to create an easily understandable model (correlations between the poverty rate and other variables are given simply by their linear
coefficients in the model) and make the prediction.  A scientist would chuckle at the fact that "linear regression" is considered to be a "machine learning"
algorithm, but hey it works and it's simple.  The machine learning algorithm that actually gave me the best score (determined by how low you can reduce
the root-mean-squared error between your predicted poverty rates and the actual poverty rates which are withheld from your knowledge) out of the ones I 
successfully tried was the Decision Tree Regression algorithm without Adaboosting.  However, that score wasn't that different from the one
obtained from linear regression.

The biggest change in decision I could have made may have been how I dealt with null values.  There were simply a lot of null values.  Some features (aka
variable or column)
had as many has 400 null values out of the 3000 or so samples (aka rows representing US counties) in the dataset, and dropping all samples with row values reduced the dataset to about 1000
samples.  I decided to simply replace each null value with the mean of the existing values in their respective feature.  It could have been handled better
perhaps by using existing categories (i.e. rural-urban continuum code, urban influence, etc.) which the samples fall under and replacing the null values by the mean of said category.

One might wonder: Couldn't a similar report be done by academics using the many tools and methods academic researchers have access to?  Or shouldn't there
have been a report like this already been done that is peer-reviewed and more sophisticated?  So what's the point of Data Science?  
The answer to both is most likely yes, but you have to remember that the field of Data Science is also meant to be support businesses whose data is not
publically available and that there are a lot of data-driven applications that use algorithms to make predictions which does not necessarily have to
translate into a written report.  There is also likely a lot of data out in the world that has not been analyzed yet, so why not let Data Scientists get to
them if academics have not?  On the other hand, machine learning can only build models based on existing data, and those models are limited to specific forms
(i.e. linear equations in the case of linear regression) - forms chosen for the ease of applicability for a wide range of data patterns.  For instance, a 
decision tree regression algorithm might output a model for a set of data that looks like a sine curve, but it won't be an actual sine curve, unless perhaps 
hypothetically you are some genius mathematician who can prove that in some limiting case, a given decision tree regression model is a sine curve.
Thus, machine learning is no substitute for the more universably applicable models that are derived from physical and mathematical reasoning, which is
primarily done in academia.  Then again, I suppose the same argument can be made for even physical theories (i.e. there are only so many different ways to
represent a "bump" shaped curve, as in Gaussians, sech^2 functions, and Lorentzians before having to resort to an infinite series - what if we encounter something
that cannot be represented by any of these so that new math needs to be invented in order to account for it?).  Actually, any arbitrary curve that is well-behaved
can probably be represented by a polynomial of either finite or infinite order, and for those that are not well-behaved, piecewise defined functions may be
adequate, so I may need to take what I just wrote back.

Ironically, one of my goals from pursuing this program had been to learn R, but someone had suggested in a forum that it is better to stick with one language
of either Python or R and get really good with it before learning the other, so I've stuck with Python for the most part this whole time.  I also don't feel
like learning R just for the heck of it, because I've already used so many different languages that at this point, I am probably better off only learning a language
when I know I will need to use it, otherwise I will be constantly struggling with confusing the syntax of one language with another.

