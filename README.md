# ml-food-price

![TensorFlow](https://img.shields.io/badge/TensorFlow-%23FF6F00.svg?style=for-the-badge&logo=TensorFlow&logoColor=white)
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
[![Google Colab](https://img.shields.io/badge/open_in_colab-blue?style=for-the-badge&logo=googlecolab&color=blue&labelColor=525252)](https://colab.research.google.com/github/MamMates/ml-food-price/blob/main/MamMates_Food_Price.ipynb)
![LICENSE](https://img.shields.io/github/license/MamMates/ml-food-price?style=for-the-badge)
![Docker Version](https://img.shields.io/docker/v/putuwaw/mammates-food-price/latest?style=for-the-badge)
![Docker Pulls](https://img.shields.io/docker/pulls/putuwaw/mammates-food-price?style=for-the-badge)

Food Price Prediction using Artificial Neural Network (ANN) and deployed using TensorFlow Serving.

Notebook: [MamMates Food Price](https://colab.research.google.com/github/MamMates/ml-food-price/blob/main/MamMates_Food_Price.ipynb)

Dataset: [Food Price Dataset](https://drive.google.com/drive/folders/1oVwvk-RV6cI0D7FvkVC2IoGrY0W_wwFH?usp=sharing)

## Features 💡

Using MamMates Food Price, you can predict the price of the food based on its name, rating, and location.

## Prerequisites 📋

- [TensorFlow](https://www.tensorflow.org/) 2.14.0 or higher
- [Docker](https://www.docker.com/) 24.0.7 or higher
- [scikit-learn](https://scikit-learn.org/) 1.3.2 or higher

## Usage ✨

If you already have Docker installed, you only need to run the following command:

- Pull the image from Docker Hub:

```bash
docker pull putuwaw/mammates-food-price
```

- Run the image:

```bash
docker run -p 8503:8503 --name ml-price putuwaw/mammates-food-price
```

- You can check that the model is already running by opening the browser and go to http://localhost:8503/v1/models/food_price

- To do prediction, you can use the following command:

```bash
curl -s https://raw.githubusercontent.com/MamMates/ml-food-price/main/example.json | curl -X POST -d @- http://localhost:8503/v1/models/food_price:predict
```

- You will get the following response:

```json
{
  "predictions": [[13661.9189]]
}
```

## Development 💻

If you want to develop this model, you can follow the steps below:

- Clone this repository:

```bash
git clone https://github.com/MamMates/ml-food-price.git
```

- Update the model by changing the saved model in the [model](model/) folder.

- Build the Docker image:

```bash
docker build -t mammates-food-price .
```

- Run the image:

```bash
docker run -p 8503:8503 --name ml-price mammates-food-price
```

- You can check that the model is already running by opening browser and go to http://localhost:8503/v1/models/food_price

- To do prediction, you can use the following command:

```bash
curl -d @example.json -X POST http://localhost:8503/v1/models/food_price:predict
```

- To stop the container:

```bash
docker stop ml-price
```

> [!NOTE]  
> If you want to learn more about TensorFlow Serving, you can read the REST API documentation [here](https://www.tensorflow.org/tfx/serving/api_rest).

## License 📝

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
