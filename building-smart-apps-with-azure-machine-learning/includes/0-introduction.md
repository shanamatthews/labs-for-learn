[Azure Machine Learning Studio](https://azure.microsoft.com/en-us/services/machine-learning/) is a cloud-based predictive-analytics service that offers a streamlined experience for data scientists of all skill levels. It features an easy to use, drag-and-drop interface for building machine-learning models. It comes with a library of time-saving experiments and features best-in-class algorithms developed and tested in the real world by Microsoft businesses such as Bing. And its built-in support for [R](https://www.r-project.org/) and [Python](https://www.python.org/) means you can build custom scripts to customize your model. Once you've built and trained your model, you can easily expose it as a Web service that is consumable from a variety of programming languages, or share it with the community by placing it in the [Cortana Intelligence Gallery](https://gallery.cortanaintelligence.com/).

In this lab, you will use Azure Machine Learning Studio to build, train, and score a model that recognizes hand-written numeric digits. You will use a real OCR data set published for academic research. After deploying the model as a Web service, you will write an [Electron](http://electron.atom.io/) client for it that lets you sketch digits on the screen and then consult Azure Machine Learning to see if it can identify the digits you sketched. You will learn how to build and train a model, as well as how to write code that leverages the model.

## Learning Objectives

In this module, you will:
- Build, train, and score a model using Azure Machine Learning Studio
- Deploy your model as a Web service so it can be accessed from code or scripts
- Call an ML Web service from the apps that you write