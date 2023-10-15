# Abstractive Text Summarization Model trained on t5 by Varad kadtan

<!-- Provide a quick summary of what the model is/does. -->

 I've developed an abstractive text summarization model using the T5 transformer architecture in PyTorch. I've fine-tuned the model on my specific dataset to create concise and coherent summaries of longer texts. This model takes advantage of transformer libraries and the power of multi-head self-attention to capture context and dependencies in the input text. It's a valuable tool for generating human-like summaries, making information extraction and condensation more efficient.
## To use my model

from transformers import AutoModelForSeq2SeqLM, AutoTokenizer

device = "cuda" if torch.cuda.is_available() else "cpu"

model_ckpt = "Varadkadtan/varad-cnn-t5"

tokenizer = AutoTokenizer.from_pretrained(model_ckpt)

model_t5 = AutoModelForSeq2SeqLM.from_pretrained(model_ckpt).to(device)


### Model Sources [optional]

<!-- Provide the basic links for the model. -->


- **Paper [optional]:** [arxiv:1706.03762]


## Uses

<!-- Address questions around how the model is intended to be used, including the foreseeable users of the model and those affected by the model. -->

Content Summarization: Your model can automatically generate concise and coherent summaries of lengthy documents, articles, or reports, making it useful for readers who want a quick overview without reading the entire text.

News Aggregation: News platforms can use your model to create summarized versions of news articles, allowing readers to stay informed on multiple topics more efficiently.

Data Mining and Information Extraction: Your model can help extract key information and insights from a large corpus of text, enabling organizations to make data-driven decisions.

Content Recommendations: Content recommendation systems can benefit from your model by summarizing content to understand user preferences and deliver personalized recommendations.

Search Engines: Search engines can use your model to provide more informative snippets for search results, helping users find relevant information faster.

Academic Research: Researchers can use your model to summarize lengthy research papers and articles, allowing them to quickly review relevant material.

Legal Documents: Legal professionals can use your model to summarize legal documents, making it easier to comprehend complex legal texts.

E-learning and Education: Your model can generate concise study materials and summaries of educational content, facilitating better understanding for students.

Content Creation and Marketing: Marketers and content creators can use your model to summarize research or competitors' content to gather insights and generate new content ideas.

Chatbots and Virtual Assistants: Your model can provide chatbots and virtual assistants with the ability to generate informative responses based on lengthy user queries or documents.

Language Translation: It can help improve the efficiency of translation services by summarizing text before translation, reducing translation time and costs.

Social Media Monitoring: Social media platforms can use your model to generate summaries of user-generated content for trend analysis and sentiment analysis.

Medical Records and Healthcare: Healthcare professionals can use your model to create concise summaries of medical records and research papers, aiding in diagnosis and decision-making.


## Evaluation

<!-- This section describes the evaluation protocols and provides the results. -->

sample_text = dataset_cnn["test"][0]["article"]

reference = dataset_cnn["test"][0]["highlights"]

gen_kwargs = {"length_penalty": 0.8, "num_beams":4, "max_length": 54}

pipe = pipeline("summarization", model="varad-cnn-t5",tokenizer=tokenizer)

print("Dialogue:")
print(sample_text)


print("\nReference Summary:")
print(reference)


model_summary = pipe(sample_text, **gen_kwargs)[0]["summary_text"]
print("\nModel Summary:")
print(model_summary)

Output:

Dialogue:
(CNN)The Palestinian Authority officially became the 123rd member of the International Criminal Court on Wednesday, a step that gives the court jurisdiction over alleged crimes in Palestinian territories. The formal accession was marked with a ceremony at The Hague, in the Netherlands, where the court is based. The Palestinians signed the ICC's founding Rome Statute in January, when they also accepted its jurisdiction over alleged crimes committed "in the occupied Palestinian territory, including East Jerusalem, since June 13, 2014." Later that month, the ICC opened a preliminary examination into the situation in Palestinian territories, paving the way for possible war crimes investigations against Israelis. As members of the court, Palestinians may be subject to counter-charges as well. Israel and the United States, neither of which is an ICC member, opposed the Palestinians' efforts to join the body. But Palestinian Foreign Minister Riad al-Malki, speaking at Wednesday's ceremony, said it was a move toward greater justice. "As Palestine formally becomes a State Party to the Rome Statute today, the world is also a step closer to ending a long era of impunity and injustice," he said, according to an ICC news release. "Indeed, today brings us closer to our shared goals of justice and peace." Judge Kuniko Ozaki, a vice president of the ICC, said acceding to the treaty was just the first step for the Palestinians. "As the Rome Statute today enters into force for the State of Palestine, Palestine acquires all the rights as well as responsibilities that come with being a State Party to the Statute. These are substantive commitments, which cannot be taken lightly," she said. Rights group Human Rights Watch welcomed the development. "Governments seeking to penalize Palestine for joining the ICC should immediately end their pressure, and countries that support universal acceptance of the court's treaty should speak out to welcome its membership," said Balkees Jarrah, international justice counsel for the group. "What's objectionable is the attempts to undermine international justice, not Palestine's decision to join a treaty to which over 100 countries around the world are members." In January, when the preliminary ICC examination was opened, Israeli Prime Minister Benjamin Netanyahu described it as an outrage, saying the court was overstepping its boundaries. The United States also said it "strongly" disagreed with the court's decision. "As we have said repeatedly, we do not believe that Palestine is a state and therefore we do not believe that it is eligible to join the ICC," the State Department said in a statement. It urged the warring sides to resolve their differences through direct negotiations. "We will continue to oppose actions against Israel at the ICC as counterproductive to the cause of peace," it said. But the ICC begs to differ with the definition of a state for its purposes and refers to the territories as "Palestine." While a preliminary examination is not a formal investigation, it allows the court to review evidence and determine whether to investigate suspects on both sides. Prosecutor Fatou Bensouda said her office would "conduct its analysis in full independence and impartiality." The war between Israel and Hamas militants in Gaza last summer left more than 2,000 people dead. The inquiry will include alleged war crimes committed since June. The International Criminal Court was set up in 2002 to prosecute genocide, crimes against humanity and war crimes. CNN's Vasco Cotovio, Kareem Khadder and Faith Karimi contributed to this report.

Reference Summary:
Membership gives the ICC jurisdiction over alleged crimes committed in Palestinian territories since last June . Israel and the United States opposed the move, which could open the door to war crimes investigations against Israelis .

Model Summary:
The Palestinians have formally joined the International Criminal Court (ICC), becoming the first country to do so.



## Model Card Contact

[Varad kadtan - kadtanvarad@gmail.com]
