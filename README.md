# NLP_Projects: 

1. NLP Analysis of Federal Reserve Meeting Minutes and Economic Indicators

This project utilizes Natural Language Processing (NLP) to extract valuable insights from Federal Reserve (Fed) meeting minutes, analyzing monetary policy communication, economic outlook, and market sentiment. By combining classical and modern NLP techniques with economic indicators, the project aims to anticipate policy changes and understand economic shifts.

Introduction

Natural Language Processing (NLP) is crucial for extracting insights from institutional communications, especially in the financial sector. The Federal Reserve's meeting minutes contain vital information on monetary policy, economic outlook, and market sentiment. Financial analysts, economists, policymakers, and investors leverage NLP to analyze trends in central bank communications to anticipate policy changes and economic shifts.

Background

Organizations utilize central bank communication analysis for several key purposes:

    Market Predictions: Financial institutions monitor central bank language for signals about future interest rate changes and economic outlook.

Policy Analysis: Economists track shifts in central bank rhetoric to understand evolving monetary policy frameworks.

Sentiment Tracking: Tracking the sentiment in monetary policy statements helps gauge the central bank's confidence in economic conditions.

Risk Assessment: Financial institutions use central bank communication analysis to identify potential economic risks and policy uncertainties.

Economic Forecasting: Analyzing the relationship between central bank language and economic indicators helps improve economic forecasts.

Project Objectives

This project was developed to:

    Build a comprehensive dataset of Federal Reserve meeting minutes from 2015-2025.

Perform sentiment analysis using both classical (VADER) and modern (Transformer-based, FinBERT) NLP approaches.

Conduct topic modeling using classical (LDA) and modern (BERTopic) NLP approaches to identify key themes and their evolution.

Extract concise summaries using FinBERT extractive summarization.

Correlate insights from Fed communications with various economic indicators to understand their relationships.

End-to-End Flow

The project follows a comprehensive end-to-end flow:

    Data Collection: Scrape FOMC meeting transcripts. 

Data Preprocessing: Clean and tokenize the text. 

Sentiment Analysis: Apply VADER (classical) and FinBERT (modern) for sentiment scoring. 

Topic Modeling: Utilize LDA (classical) and BERTopic (modern) to identify key discussion themes. 

Extractive Summarization: Generate summaries using FinBERT. 

Data Collection

The dataset consists of FOMC meeting transcripts from 2015-2025, excluding COVID-era years (2020-2021).

    Source: FOMC transcript links were collected from the Federal Reserve Website (both current and historical archive pages). 

Methodology:

    User input was used to define a custom start and end date for the data collection. 

Regular expressions (regex) were employed to parse relevant URLs matching meeting minute formats (e.g., 

minutesYYYYMMDD.htm). 

BeautifulSoup was used to scrape the transcript text from the main 

div of each webpage. 

Structured data (URL, Date, Year, Month, Day, Content) was compiled into a DataFrame named 

df_transcripts. 

Exploratory Data Analysis Highlights:

    From 2015 to 2023, the Federal Reserve held approximately 8 meetings annually, with no data for 2020 and 2021 due to the COVID-19 pandemic. 

The number of meetings in 2025 is lower as the year is not yet complete. 

Transcript lengths peaked in 2019, indicating more extensive discussions, and have generally shortened after 2021, possibly due to more concise meetings. 

Text Preprocessing

Text preprocessing involved cleaning the raw transcript content to enhance the quality of NLP analysis.

    Tools: spaCy was used for text cleaning. 

Custom Cleaning Function (minimal_clean): This function was applied to remove:

    URLs (http, www) 

Email addresses 

Extra spaces 

HTML tags were also removed using BeautifulSoup. 

The cleaned text is stored in a new column called 

cleaned_text in the df_merged DataFrame. 

SNR Ratio Analysis:

    Transcripts are consistently labeled as "Low" or "Medium" clarity, with a slight shift towards "Medium" in later years. 

Before 2020, the SNR ratio was more volatile, suggesting noisier communication. 

From 2022 onwards, SNR ratios show improved clarity, consistently remaining in the "Medium" range. 

Text cleaning smoothed the SNR ratio trend, indicating effective noise reduction. 

No transcript achieved a "High" SNR ratio, implying that even the clearest communications were not exceptionally clear. 

Sentiment Analysis

Classical Approach (VADER)

VADER (Valence Aware Dictionary and sEntiment Reasoner) was used to extract sentiment scores (positive, negative, neutral, compound) for each transcript.

    Overall Sentiment: The compound sentiment score distribution is heavily skewed towards 1, indicating a highly positive overall tone in the transcripts. 

Trend: While generally stable and positive, there's a very slight downward trend in the average yearly sentiment score from 2016 to 2025, suggesting a subtly less positive tone in recent years. 

Word Clouds: Key terms like "Federal Reserve," "Committee," "Inflation," "Rate," and "Labor Market" consistently appear, highlighting stable communication focus. 

Shift in Focus: More recent years (2024-2025) show increased emphasis on "Director," "Division," and "Staff," potentially indicating shifts in operational focus or discussion style. 

Modern Approach (FinBERT)

FinBERT (a BERT model fine-tuned for financial text) was used for transformer-based sentiment analysis.

    Overall Sentiment: Most FinBERT sentiment scores are below zero, indicating a generally cautious or slightly pessimistic tone in Federal Reserve meeting transcripts. 

Persistent Terms: Words like "inflation," "rate," "market," and "Federal Reserve" consistently appear in word clouds across all years, confirming their continuous importance to the committee. 

Fluctuating Mood: Occasional brief spikes into positive sentiment occur but are not sustained; the general mood consistently returns to neutral or negative. 

Increased Complexity: Recent years (2023-2025) introduce terms like "participants," "expected," and "risk," suggesting more complex economic discussions or heightened uncertainty. 

Dominant Negative Sentiment: The histogram shows that most sentiment scores fall within the -0.3 to -0.4 range, indicating a moderate negative bias. 

Topic Modeling

Classical Approach (LDA)

Latent Dirichlet Allocation (LDA) via Gensim was used to identify key topics and their evolution.

    Coherence Score: A topic model with 5 topics yielded the highest coherence score (~0.362), representing the best balance of clarity and topic separation. Adding more topics did not improve the model. 

Topic Distribution: Topic 4 (containing "rate," "inflation," "market," "committee," "federal") is the most dominant theme, appearing in over 40 documents. 

Least Common Topic: Topic 1 is the least common, suggesting it is either too narrow or only relevant to a few documents. 

Topic Evolution:

    From 2015 to 2020, Topic 4 consistently dominated discussions. 

Starting in 2022, Topic 2 ("inflation," "rate," "participant," "market," "federal") became more frequent, indicating a shift in focus. 

The emergence of Topic 3 and Topic 1 in later years signifies increased diversification or detail in discussions. 

Modern Approach (BERTopic)

BERTopic was applied for transformer-based topic modeling.

    (Add specific insights from BERTopic analysis if available in the source, as the current source mainly covers LDA for "Topic Modeling" and does not specify BERTopic results beyond being a "Modern NLP Approach - Topic Extraction" and "Compare with classical LDA topic modeling results" ). If no specific results were provided for BERTopic in the original content, this section can be a placeholder or mention that it was part of the methodology.)

Economic Insights

Correlation analysis was performed between sentiment scores and economic indicators:

    Positive Sentiment & Compound Score: The compound score is highly positively correlated with positive sentiment (0.76), intuitively showing that more positive words lead to a higher overall score. 

Negative Sentiment Impact: Negative sentiment (neg) exhibits a strong negative correlation with both compound (-0.52) and positive sentiment (pos) (-0.35), meaning increased negativity reduces overall and positive sentiment scores. 

Neutral Sentiment Stability: Neutral sentiment (neu) shows weak correlations with other sentiment scores and almost zero correlation with most economic indicators, indicating its relative stability. 

Compound Sentiment & Unemployment: There is a positive correlation (0.32) between compound sentiment and unemployment, which might reflect delayed reporting or contextual factors. 

CPI & Fed Funds Rate: CPI (Consumer Price Index, a measure of inflation) and FedFundsRate (Federal Funds Rate) are highly correlated (0.87), aligning with the economic principle that interest rates often follow inflation trends. 

Negative Sentiment & Fed Funds Rate: Negative sentiment is positively correlated with the FedFundsRate (0.31), suggesting that discussions tend to be more negative when interest rates are high, possibly due to concerns about tighter economic policy. 

Key Findings

    Modern NLP approaches (like FinBERT) provide deeper insights compared to classical methods (like VADER). 

The language used in FOMC meeting minutes demonstrates predictive power regarding economic trends. 

    Despite variations, core topics like inflation, interest rates, and the labor market remain central to Fed communications.

    Sentiment in Fed communications, particularly when analyzed with FinBERT, tends to be cautious or slightly pessimistic, especially during periods of high interest rates.

Future Work

    Fine-tune FinBERT for even more precise sentiment analysis on financial texts. 

Implement real-time analysis of new meeting minutes. 

Develop and deploy an interactive dashboard for visualizing insights.
