# HeQ - Hebrew Question Answering Dataset

## Summary
HeQ is a question answering dataset in Modern Hebrew, consisting of 30,147 questions.

## Introduction
The dataset follows the format and crowdsourcing methodology of SQuAD (Stanford Question Answering Dataset) and the original ParaShoot. A team of crowdworkers formulated and answered reading comprehension questions based on random paragraphs in Hebrew. The answer to each question is a segment of text (span) included in the relevant paragraph. The paragraphs are sourced from two different platforms: (1) Hebrew Wikipedia, and (2) Geektime, an online Israeli news channel specializing in technology.

## Question Features
Two types of questions were collected:
1. Answerable questions (21,784): Questions for which the answer is present in the paragraph.
2. Unanswerable questions (8,363): Questions related to the paragraph's content, where the paragraph provides a plausible answer, but the answer is not explicitly included.

## Quality Labels
As part of ongoing quality control during the collection process, and additional checks on the test and validation sets, 28% of the final data was manually verified. Of the final data, 16% received one of the following labels:

- Verified: Questions that passed the threshold and were relatively easy, with wording exactly or similar to the relevant sentence in the paragraph, or very common questions.
- Good: Questions with wording that was significantly different (lexically or syntactically) from the wording of the relevant sentence in the paragraph.
- Gold: Questions that involve inference-making.

The Geektime dataset also includes the following labels:
- Deixis: Questions where the answer is an expression of time that depends entirely on the context (e.g., "last year," "tomorrow," etc.).
- Second: Questions where the answer is written in the second person ("you").
- Checked: Manually validated questions that did not receive a label based on their quality.

## Additional Answers
After splitting the data, the test and validation subsets underwent additional processing. In cases where there were multiple correct answer spans for an answerable question, the additional possible answers were added to both subsets to enhance robustness. For example, if the answer appears in quotation marks, another possible answer could be the same answer without the quotation marks. Another example involves answers that may or may not include prepositions preceding the content or appositions. Each answerable question in the test and validation sets received 0 to 6 additional possible answers.

## Dataset Statistics
The table below shows the number of answerable and unanswerable questions in each source and split of HeQ:

|                  | Hebrew Wikipedia | Geektime |
|------------------|------------------|----------|
| Answerable       | 9987             | 9667     |
| Unanswerable     | 3533             | 3955     |
| Train            | 13622            | 13622    |
| Val              | 536              | 522      |
| Test             | 545              | 527      |

The table below shows the number of unique questions, paragraphs, and articles in each source and split of HeQ:

|                  | Hebrew Wikipedia | Geektime |
|------------------|------------------|----------|
| Questions        | 13520            | 13622    |
| Paragraphs       | 2006             | 2395     |
| Articles         | 1481             | 2317     |

## Code
The `Quality_control_Hebrew_QA.ipynb` file is a notebook used to extract specific data features that formed the basis for the validation process. The code for the web-based annotation interface used in this project can be found [here](link-to-the-code).

### Paper
https://u.cs.biu.ac.il/~yogo/heq.pdf

### Model
https://huggingface.co/amirdnc/HeQ

## Contributors
HeQ was annotated by Webiks for MAFAT, as part of the National Natural Language Processing Plan of Israel. 
Contributors: Hilla Merhav Fine (Webiks), Roei Shlezinger (Webiks), Amir David Nissan Cohen (MAFAT)
Advisors: Reut Tsarfaty, Kfir Bar, Yoav Goldberg

Acknowledgments
We would like to express our gratitude to Omri Keren and Omer Levy, the creators of the original ParaShoot, the first question answering dataset in Hebrew, who also contributed to this project their annotation interface.
We are also grateful to Geektime, for allowing us to annotate their articles and share the data as a public dataset.
