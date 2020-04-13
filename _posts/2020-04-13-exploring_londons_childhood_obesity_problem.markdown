---
layout: post
title:      "Exploring London's Childhood Obesity Problem"
date:       2020-04-13 09:42:43 -0400
permalink:  exploring_londons_childhood_obesity_problem
---


For my final portfolio project, I decided to try and build an app related to public health. London has particularly high proportion of school-aged children aged 4-5 and 10-11 who are overweight and obese. I wanted to focus on shining a light on this issue by sharing the data available from Public Health England's [fingertips profile](https://fingertips.phe.org.uk/). I visualised the finished product to be a chart that will enable users to browse and display and compare data across different areas in London. 

I started by downloading the childhood obesity profile in London in a CSV format.  This includes a breakdown of prevalence rates in 32 different London Boroughs* for the sets of age groups (4-5 year olds and 10-11 year olds). 

I then loaded and used the datasets to build my Rails API. At this stage, I learned about DB Browser for sqlite along with the various Rake Tasks which I used to create my database. 

Once my API was up and running, I went straight into building the frontend with React/Redux. 

The Redux store holds the entire state of the application. I decided to use Redux as I knew that I would need a number of components to access and use this state. 

Thinking in terms of *actions* and *reducers* in Redux also helped me understand separation of concerns or responsibilities and subsequently organise my code. 

A crude representation of the structure goes like this: 

* Action fetches data from API and is called after componentDidMount()
* This sets off the Reducer which takes the old state and turns it into the new state 
* New state is held in the Store which now contains the API data (i.e. the London Childhood Obesity dataset broken down by London Boroughs and age)
* This data can be access by component containers as props by using mapStateToProps() 

Sticking to the topic of convention and organising code, it also helped to keep reminding myself that while building my React components, **only the containers should know Redux**. Components can access the data by passing the data that we need down as props as per below:

```
class ChartsContainer extends React.Component {
  componentDidMount() {
    this.props.fetchLocalAuthData();
  }

  render() {
    return (
      <div className="section-charts-container">
        <div className="page-title">
          <h1>Prevalance of Childhood Obesity in London 2018/19</h1>
          <p>The chart below shows the average prevalence of childhood obesity
          across London in %. Find out more about the prevalence of childhood
          obesity in specific London Boroughs by selecting a Local Authority
          below.</p>
        </div>
        <div>
          {this.props.localAuthData.length > 0 && (
            <AreaDropdown londonData={this.props.localAuthData} />
          )}
        </div>
      </div>
    );
  }
}

const mapStateToProps = (state) => {
  return {
    localAuthData: state.localAuthData.localAuthData,
  };
};

const mapDispatchToProps = (dispatch) => {
  return {
    fetchLocalAuthData: () => dispatch(fetchLocalAuthData()),
  };
};

export default connect(mapStateToProps, mapDispatchToProps)(ChartsContainer);
```

**Conclusion**

I thoroughly enjoyed learning and building this React/Redux application although I have had a lot of challenges along the way (including the fact that we are in the middle of a pandemic). There is a lot to learn but frontend development as a career, specifically in React is looking like an attractive and enjoyable path to go into. 



*The data for City of London (33rd London Borough) is combined with Hackney data due to small numbers. 






