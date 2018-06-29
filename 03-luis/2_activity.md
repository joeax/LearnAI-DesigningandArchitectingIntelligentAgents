# 3.2: Activity (ADS/Wireframe) - LUIS Design 

An Architecture Engagement contains the following general phases. The phases covered by this lab are in italics: 

 <table style="width:100%">
  <tr>
    <th><b>Phase</b></th>
    <th><b>Audience</b></th>
    <th><b>Deliverable</b></th>
  </tr>
  <tr>
    <td>Discovery</td>
    <td>Business Organization, Technical Team</td>
    <td>Business Requirements</td>
  </tr>
  <tr>
    <td>Envisioning</td>
    <td>Business Organization, Technical Team</td>
    <td>Business-Ready Presentation</td>
  </tr>
  <tr>
    <td><i>Architecture Design Session</i></td>
    <td><i>Internal and External Technical Teams</i></td>
    <td><i>Wireframe Diagram, Data Flow Diagram</i></td>
  </tr>
  <tr>
    <td>Proof of Concept</td>
    <td>Internal and External Technical Teams</td>
    <td>Functional Prototype</td>
  </tr>
  <tr>
    <td>Implementation</td>
    <td>Internal and External Technical Teams</td>
    <td>Project Oversight Document</td>
  </tr>
  <tr>
    <td>Handoff</td>
    <td>Business Organization, Internal and External Technical Teams</td>
    <td>All previous documents, follow-up strategy document</td>
  </tr>
</table> 

This design-based lab will allow you to work in groups to explore the principles of LUIS Schema design. The output of the lab is for the class to create a set of artefacts that articulates the Intent design, Entity and Utterance design for a fictitious organization as defined in a case study. You will use these artefacts to  build your Capstone Project.

## Objectives
In this lab, you will be separated into groups as directed by the instructor. Each group will be given an assignment to complete which will involve the following three objectives:

- Bot Flow Logic with Intents.
- Designing Entities.
- Managing Utterances.

## Case Study

A hotel chain CEO recently announced in a trade magazine that she is looking to enhance the customer experience by augmenting their in-person concierge service by embedding bot capabilities into their member services mobile app. The hotel guest reservations are held within an Azure SQL Database which contains the dates and the hotel location of the guest that is presented to the application. The bot is intended to handle the common request that guest will make such as setting up wake up calls, ordering services such as a pool cabana or spa session, or handling cab reservations with their in-house cab company. Therefore, the bot should be able to offer to book these services, providing a choice on dates and durations. The intention is to free up the real concierge’s time to focus on informing guest about the local area using local knowledge. It is critical that access to the bot is secured. The hotel chain is a Microsoft Shop. Their network is setup using AD, the databases using SQL Server and cloud applications developed in .Net in Azure. The CFO and CIO has made budget available for this project to be delivered within 6 months.

## Exercise 1: Bot Flow Logic with Intents

![Defining a Bot Personality Profile](./resources/assets/sess_3.1_Lab_1.1.jpg)

Using the materials above, define the LUIS domains and intents that you can identify from the case study for a Architecture Design Session (ADS). As a challenge try to map the high level conversation patters to each of the intents that you identify.

## Exercise 2: Designing Entities 

![Designing Entities ](./resources/assets/sess_3.1_Lab_1.2.jpg)

Update your ADS Document to select three intents from the previous exercise and define the entities that will be used. 

## Exercise 3: Designing Utterances

![Designing Utterances](./resources/assets/sess_3.1_Lab_1.3.jpg)

Using the same three intents from the previous exercise, define the utterances that would be used to capture the entities defined in the previous exercise, and update your ADS document accordingly. What would you use to improve the utterance accuracy?

Finalize your ADS session for technical presentation. Save that in the same location as the Bot Design lab exercises for inclusion into the Capstone project.

Back to [README](./README.md)