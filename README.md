# Resume CV Summarizer

I've created a CV summarizer AI model using Spacy NER (Named Entity Recognition) model.

## Demo
Before submitting pdf resume file:

![Website Screenshot](https://github.com/ishtiuk/Resume-CV-Summarizer/blob/master/images/ui_before.png?raw=true)

After submitting pdf resume file:

![Website Screenshot](https://github.com/ishtiuk/Resume-CV-Summarizer/blob/master/images/ui_after.png?raw=true)

## Description

The project involves training a Spacy NER model to detect various named entities in CVs/resumes, such as:

- Name
- Skills
- Degree
- Awards
- Contact
- Location
- Language
- Worked As
- University
- Designation
- College Name
- Email Address
- Linkedin Link
- Certification
- Graduation Year
- Year Of Graduation
- Companies Worked At
- Years Of Experience

My whole training process includes the following steps:

- Training the Spacy blank English NER model on a total of 1214 CV/resume data to detect named entities.
- Preprocessing the training data and converting it into Spacy Docbin objects.
- Saving the training data and testing data as "train_data.spacy" and "test_data.spacy" respectively.
- Training the model on Google Colab with a Tesla T4 16GB GPU using Spacy Transformer.
- Saving the trained model outputs in two separate folders: "model-best" and "model-last". The "model-best" folder contains the best model during training with an accuracy score of 84%.

## Requirements

The project requires the following dependencies:

- Python 3.8 or up
- Spacy
- Spacy Transformer
Make sure to install these dependencies before running the project.

## Setup

Before training the model, you need to set up the `config.cfg` file. Run the following command on your notebook:

```bash
!python -m spacy init fill-config base_config_path/base_config.cfg config_path/config.cfg
```

## Training

To start the training process, use the following command:

```bash
!python -m spacy train config_path/config.cfg --output your_output_path/output --paths.train /train_path/train_data.spacy --paths.dev /test_path/test_data.spacy --gpu-id 0
```

## Usage

Once the project is set up and the model is trained, you can use the CV summarizer by calling the appropriate functions in your code. The trained model will process a given CV or resume text and extract the relevant named entities.

```python
import spacy
import spacy_transformers

# Load the trained model
nlp = spacy.load("path/to/model-best")

# Process a CV or resume text
text = "..."
doc = nlp(text)

# Access the extracted named entities
entities = [(ent.text, ent.label_) for ent in doc.ents]

for ent, label in entities:
  print(label.ljust(20, " "), "   ->>  ", ent, end="\n")

# Perform further analysis or summarization based on the extracted entities
```

## Contributing

Contributions are welcome! If you encounter any issues or have suggestions for improvements, please open an issue or submit a pull request.

## Acknowledgements

This project was inspired by the need for automating the process of summarizing CVs and resumes. Special thanks to the Spacy and spacy_transformer teams for their excellent libraries and resources.

## License

This project is licensed under the [MIT License](https://github.com/ishtiuk/Resume-CV-Summarizer/blob/main/LICENSE).
