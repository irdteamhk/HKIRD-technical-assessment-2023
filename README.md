# HKIRD Technical Assessment 2023

Hello and congratulations on making it to this stage of the interview process with the HKIRD team! We believe in a hands-on approach to assess the skills and knowledge of our potential candidates. This assessment will provide an opportunity for you to showcase your expertise.

Below are the instructions for the tasks you need to complete. Please read them carefully and ensure all requirements are met. There are two parts the assessment. 

# Assessment Part 1: Data Analysis, Machine Learning Model Training and Container Deployment

## 1(a): Data Handling and Model Training

### Requirements:

1. **Data Extraction**:
    - Begin by unzipping the `data.zip` folder.
    - Within the unzipped `data` folder, you'll find a `train` subfolder containing the training set images.

2. **Image Naming and Labeling**:
    - The class label of each image can be deduced from its parent folder. For instance:
      - Image at path `train/0/43.jpg` corresponds to class label 0.
      - Image at path `train/5/94.jpg` corresponds to class label 5.

3. **Data Analysis, Cleaning, and Transformation**:
    - Perform an analysis of the dataset.
    - Carry out necessary data cleaning and transformations.
    - Ensure your transformations cater for the potentially varying image sizes.

4. **Model Training**:
    - Build and train a machine learning or deep learning model using the transformed dataset.
    - Ensure that you have implemented measures to ensure you are not overfitting and can perform decently with unseen data.

5. **Jupyter Notebook**:
    - All the above tasks should be performed in a Jupyter Notebook (.ipynb).
    - The notebook should be structured, with appropriate analysis and documentation, to showcase your skills and proficiency.
    - Once completed, save the notebook. Also, convert the notebook into a .html file using the command:
    ```bash
    jupyter nbconvert <your_notebook_name>.ipynb --to html
    ```
    OR
    - In your jupyter notebook, File --> Save and Export Notebook As --> HTML

## Part 1(b): Model Deployment

### Requirements:

1. **FastAPI Deployment**:
    - By the end of Part 1, you should have a trained model.
    - Your task is to serve this model using FastAPI.

2. **Docker Containerization**:
    - Containerize your FastAPI application using Docker.
    - The container should be set up such that it can execute the script provided below, which fetches predictions for images located in `./data/sample_test folder`.
    - Build your image and run using `docker run --rm -p 1234:80 hkird_submission`.
    - Please strictly follow the image name, host port and container port above.

3. **Testing Your API**:
    - Make sure you successfully run `docker run --rm -p 1234:80 hkird_submission`
    - Pay close attention to the url below.
    - Ensure the API correctly returns predictions when running the given script:
    ```python
    import requests

    image_file_path = "./data/sample_test/54.jpg"

    url = "http://127.0.0.1:1234/predict/"

    with open(image_file_path, "rb") as image_file:
        files = {"file": image_file}
        response = requests.post(url, files=files)

    prediction = response.json()['prediction']
    # example prediction
    print(prediction)
    > 3
    ```
    - Your API must be built in a way such that the above code can be executed without problem.


4. **Exporting Docker Image**:
    - Once everything is set up, export your Docker image as a hkird_submission.tar file.
    - You MUST use `docker save hkird_submission -o hkird_submission.tar` to prevent different OS save and loading problems.
    - Please do sufficient testing that loading your .tar file and running the image also works using `docker load -i hkird_submission.tar`
    - Please zip the .tar file before uploading it. This will help keep the size of the .tar file below 1GB which is important for submission.
  
## Part 1(c): Planning for Production (skip this for AI Engineer role)

Please skip this section if you are applying for the AI Engineer role.

By this point, you are able to train a model and serve it in a simple container using FastAPI and Docker. Imagine that you are in a project team and the team wishes you productionize your model so that it can be used by the business user’s application. You received news that your model must be able to have a high amount of throughput, making many predictions throughout the day. Knowing the rough requirements, you decided to use cloud services for the flexibility to scale up and down. 
Your job as the Machine Learning Scientist is to brainstorm a cost efficient and scalable prototype that demonstrates the (potential) ability to provide your model’s services at the required scale. Of course you will also need to explain the plan once you are done.

**Some requirements for your prototype solution:**
* An architectural diagram
* Cloud based (doesn’t matter which cloud)
* Storage for your data and model
* Services deployed on K8s cluster
* There’s no model performance requirement, but you should have some mechanisms to make it better in the future API for your users to try

You are required to prepare a PowerPoint presentation that covers the above requirement and explain your decisions. There is no constraint on the format of the PowerPoint and level of technicality. However, hands on technical work for this part is purely optional.

# Assessment Part 2: China LLM Research and Showcase

While the world has seen the many strides and development of OpenAI and ChatGPT, not much has been covered in terms of LLM development in China. However, for insurance companies, Mainland China Visitors (MCV) customers are a fast growing segment of the insurance business. Given this fact, it is worthwhile for us to also research the capabilities of China based LLMs and how they can help our insurance business to continue to serve and grow the MCV market. 

## 2(a): Decoding Developments & Capabilities of LLM in China

Please ensure to cover the following during your research:

* **Latest breakthroughs in China-based LLMs:** Shed light on the current state-of-the-art capabilities of Chinese LLMs. Demonstrate these capabilities by in a Python Jupyter Notebook with some example data, if possible relate them to some insurance use cases. You are not required to build an entire chatbot. 

* **Implications for the Insurance Sector:** Correlate these LLM capabilities with our insurance business. How can they benefit our agents and customers? Develop a few meticulously detailed use cases explaining how these technologies can be integrated into practical applications to enhance service delivery.

* **Challenges & Comparisons:** Address any prevailing limitations or shortcomings of these Chinese LLMs. Further, provide a comparative analysis against the Chinese capabilities of the globally recognized OpenAI GPT models. Your comparison should draw from both strengths and weaknesses of the two models, hence providing us with an objective overview.

For this part, you are required to submit your Jupyter Notebook in .ipynb and .html format and also a PowerPoint. If you are doing part 1(c), you may append to the same PowerPoint.

# Submission Instructions:

Please ensure that all the below files are included in your submission:

1. Your Jupyter notebook (.ipynb) and HTML version of your Jupyter notebook (.html) for part 1
2. The Docker saved image (hkird_submission.tar) or zipped
3. PowerPoint (.ppt) file for part 1(c) (skip this for AI Engineer role)
4. Your Jupyter notebook (.ipynb) and HTML version of your Jupyter notebook (.html) for part 2
5. PowerPoint (.ppt) file for part 2(a)
6. A details.json file with the following details (example below):

```python
{
    "name":"Chan Tai Man",
    "email": "chantaiman@gmail.com
}
```

Package all the above files into a .zip file, and create a new repository on GitHub (sign up for an account if you don't have), configure [GitHub LFS](https://docs.github.com/en/repositories/working-with-files/managing-large-files/configuring-git-large-file-storage) and upload the .zip file in the repository using command line Git or GitHub Desktop. It is essential that you make sure your .tar file is not corrupted during uploading of the .zip file. Lastly, send an email to irdmanulife@gmail.com with the title subject "HKIRD Technical Assessment 2023 Repository-(YOUR NAME)" and include the link to your repo. You must submit your work within 5 days of beginning the assessment

Best of luck with the assessment! We look forward to reviewing your submission.
