# Enigma
EDA and some light modeling of an Enigma dataset on H1B visa applications

**Data**:

Dataset can be found here (I'm not uploading 600mb to Github): 
https://www.kaggle.com/evangelize/h1b-visa-applications

First off, this data is probably flawed and not what you're looking for. Do with it what you will.

Data was sourced from Enigma:

https://public.enigma.com/browse/collection/h-1-b-visas/d582dfbd-4329-4b5e-b0c9-39149f5dd546

It contains data from 2005 to 2017. I downloaded each individual dataset, kept the columns that were continuous across each year, cleaned some of the data, normalized salaries, added a 'year' column to separate datasets, and reuploaded here. Obviously the data isn't perfect and neither is the cleaning. Case status is super janky. There's a bunch of small statuses that I'm not sure about.

It looks like there's something super wrong with the data around 3rd quarter 2009 and I'm not sure if it's due to the recession, the fact that there are two separate datasets for 2009 that are titled differently from the rest, or the data is just fucked up. Soc code changes from https://www.immihelp.com/visas/h1b/lca-occupation-codes.html to https://www.bls.gov/oes/current/oes152041.htm after 2009 BUTTTT I think halfway through 2011 the code convention also changes because the software engineering ones change. There's a bunch of applications that have total shenanigan fuckery going on (salaries in the tens of millions, applying for a hundred thousand workers at once) and they usually get rejected or withdrawn pretty instantly but it's messing with the distributions. I'm including them for the purposes of predictive modeling but if you want to look for trends you should remove them.

When normalizing salary, I assumed 40 hour weeks, 52 weeks a year, 12 months a year of work. This kinda messes up with some professions (some professors are paid really highly by the hour to lecture, I think some consultants have crazy high hourly wages).

I don't think this dataset captures the full H1B application process, this has like 85% of applications being certified, when I'm sure the number is much, much lower. All the sources I used to check for the number of H1B acceptances per year say under 100k a year.

**EDA**:

First, I just want to show you that 3rd quarter 2009 is janked. Here are the number of applicants over time, with slight overlap on 3rd quarter 2009. 

![Imgur](https://i.imgur.com/HetWTXx.png)

![Imgur](https://i.imgur.com/unAk8th.png)

Clearly something's wrong. 

Referring back to the changing job codes - here's before and after 2009 again. 

Actually eh I think I'm going to go and try to aggregate a little bit. 

Marimekko Chart: 
For more information on what a Marimekko chart is and how to make one, see http://duelingdata.blogspot.com/2018/08/marimekko-slope-chart.html (this is my boss, he's dope)
