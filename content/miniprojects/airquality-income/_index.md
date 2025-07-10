---
title: "Income and Air Quality"
date: 2025-07-09
---

## Topic 

> ***What is the correlation between air quality and wealth in the U.S.?***

## Our Hypothesis

We compared the AQI with the annual income of people in counties across the US in 2023. We thought that there would be an inverse relationship between income and  air quality, since people with more economic resources have more options to live in areas with less pollution than individuals who have less finanical assets.

## Data Acquisition

The US Envirormental Protection Agency provided annual [data](https://aqs.epa.gov/aqsweb/airdata/download_files.html#Annual) on the air quality (AQI) of hundreds of counties in the United States. This had data on the *Median AQI*, *90th Percentile AQI*, and even numbers of *Very Unhealthy Days*. We chose to use the Median AQI because it would be less affected by incidents such as wildfires, making it a better indicator of normal air quality.

## Data Preprocessing

We found data on incomes for each county on the [BEA](https://www.bea.gov/data/income-saving/personal-income-county-metro-and-other-areas) (Bureau of Economic Analysis) website. This had entries for *every* county in the US. However, the formatting was not ideal. Each entry only had the county name, not the state the county belonged to. The formatting looked something like this:
<body>
  <div class="t">
    <table>
      <thead>
        <tr>
          <th>Jurisdiction</th><th>2021</th><th>2022</th><th>2023</th>
          <th>Rank 2023</th><th>% Δ 21–22</th><th>% Δ 22–23</th><th>Rank Δ</th>
        </tr>
      </thead>
      <tbody>
        <tr><td>United States</td><td>64,460</td><td>66,244</td><td>69,810</td><td>—</td><td>2.8</td><td>5.4</td><td>—</td></tr>
        <tr><td><strong>Alabama</strong></td><td>50,483</td><td>51,683</td><td>54,209</td><td>—</td><td>2.4</td><td>4.9</td><td>—</td></tr>
        <tr><td>Autauga</td><td>49,174</td><td>49,811</td><td>53,079</td><td>10</td><td>1.3</td><td>6.6</td><td>6</td></tr>
        <tr><td>Baldwin</td><td>56,285</td><td>57,621</td><td>60,969</td><td>4</td><td>2.4</td><td>5.8</td><td>12</td></tr>
        <tr><td>Barbour</td><td>40,954</td><td>41,031</td><td>41,531</td><td>56</td><td>0.2</td><td>1.2</td><td>58</td></tr>
        <tr><td>Bibb</td><td>37,362</td><td>38,196</td><td>39,835</td><td>64</td><td>2.2</td><td>4.3</td><td>35</td></tr>
        <tr><td>Blount</td><td>42,975</td><td>44,063</td><td>45,021</td><td>38</td><td>2.5</td><td>2.2</td><td>52</td></tr>
        <tr><td>Bullock</td><td>34,068</td><td>33,429</td><td>36,061</td><td>67</td><td>-1.9</td><td>7.9</td><td>1</td></tr>
        <tr><td>Butler</td><td>45,438</td><td>47,502</td><td>49,192</td><td>22</td><td>4.5</td><td>3.6</td><td>41</td></tr>
        <tr><td>Calhoun</td><td>43,215</td><td>42,668</td><td>44,737</td><td>40</td><td>-1.3</td><td>4.8</td><td>25</td></tr>
        <tr><td>Chambers</td><td>39,269</td><td>39,447</td><td>40,735</td><td>62</td><td>0.5</td><td>3.3</td><td>43</td></tr>
        <tr><td>Cherokee</td><td>44,590</td><td>44,563</td><td>45,099</td><td>36</td><td>-0.1</td><td>1.2</td><td>59</td></tr>
        <tr><td>Chilton</td><td>42,839</td><td>43,454</td><td>46,120</td><td>31</td><td>1.4</td><td>6.1</td><td>9</td></tr>
      </tbody>
    </table>
  </div>
</body>

This would become a problem because we would need to uniquely match each entry in the *Incomes* data to entries in the *AQI* data. County names were not enough because they would frequently repeat. For example, there were *31 counties* named “Washington.” 

To solve this, we needed to create a column to specify the state of each county. We created a script to go through row by row and look for state names. Then it would label the counties after that with that state until we reached another row with a state name. 

Multiple team members did these cleaning steps differently. However, our resulted data ended up varying in lengths, ranging from 720 to 740 entries. This discrepency was due to county names being the name of a state, such as *Arkansas, Arkanasas*.

After some debugging, we combined both the income and air quality dataset into one comphrensive file.

## Data Modeling

We used a linear regression plot to graph our data, producing the following image:
![](linear-regression-plot.png)<!-- {"width":220} -->

## Outcome

The resulting correlation was **0.0132**. We expected a medium-strong inverse correlation, and we believe this difference was due to the fact that counties hold tens of thousands to millions of people. With such a large population, is it very possible that there exists both affulent and decrepit neighborhoods within the counties. When taking the median AQI and average income of a county, the fine details often gets lost. To produce a more accurate result, it is a good idea to use smaller units of measurement like cities or city districts for future tests.

<div style="width: 716px; height: 350px; overflow: hidden; position: relative;">
    <iframe src="/income_aqi_full_data.html" 
            style="border: none; 
                   position: absolute; 
                   width: 1200px; 
                   height: 580px; 
                   transform: scale(0.7); 
                   transform-origin: 0 0;" 
            scrolling="no">
    </iframe>
</div>