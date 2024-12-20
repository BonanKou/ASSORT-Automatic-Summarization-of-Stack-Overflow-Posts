This repository contains code, models, and data to use ASSORT_S and ASSORT_IS.

## Code
To use ASSORT_s, go to `code/assort_s.ipynb`. To use ASSORT_is, go to `code/assort_is.ipynb`. One just needs to input the information of the SO post that needs to be summarized and the model would run to output a possibility of each sentence being important.

## Models
The `models` folder contains models trained on our dataset. Specifically, `1.pkl`, `1.pkl`, and `1.pkl` are used to classify sentences from SO posts with different question types. `question_classifier.pkl` is used to classify questions.

## Dataset structure
Our dataset is in `dataset.pkl`. Specifically, we explain each field in the json below:

- `answer_body` : Body of the answer post (String)
- `question_id` : PostID of the parent question (Integer)
- `question_type` : Question type of the parent question. 1 for conceptual questions, 2 for how-to questions, 3 for debug-corrective questions (Integer)
- `question_tags`: Question tags (Array of String)
- `question_title` : Title of the parent question (String)
- `sentences` : List of sentence-level details, object structure below (Array of Objects)

| Field        | Type           | Description                          |
| ------------ | -------------- | ------------------------------------ |
| `sentence`   | String         | The sentence itself                  |
| `truth`      | Integer (0/1)  | 1: Summative, 0: Trivial             |

Example:

```json
{
    "answer_id": 12345,
    "answer_body": "This is an example answer body.",
    "question_id": 67890,
    "question_type": 1,
    "question_tags": ["Java"],
    "question_title": "How to use JSON in Python?",
    "sentences": [
        {
            "sentence": "You can use the json module to parse JSON data.",
            "truth": 1
        },
        {
            "sentence": "It's part of the standard library.",
            "truth": 0
        }
    ]
}
```
