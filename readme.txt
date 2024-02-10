Extractive Text Summarization usng SVM, KNN, Decision Tree

Using FNS2020 dataset, it is not labelled, so initially, we do labelling, and using this labelled dataset(format - sentence, label csv file), we do preprocessing on all files and generate preprocessed data(format - sentence, label, preprocessed sentence csv file), using this as input for next step i.e, feature extraction, in feature extraction we are doing sentence length, sentence position,no. of proper nouns, no. of adjectives, tf-isf, cosine similarity on all files(annual_reports) of training folder in FNS2020.Output of ths stage is of format sentence, label, preprocessed_sentence,sentence_length,sentence_position,proper_nouns,adjectives,tf_isf,cosine_similarity,file_name csv file

Using this feature extractions of annual_reports, now we are doing undersampling(downsampling) i.e, balancing class distributio, because majority of class label is '0', by using undersampling, we can bring the ratio of sentences labelled 0 and 1 as 1:1 ratio.

Now, giving this sampled feature extraction(drop sentence, preprocessed_sentence within dataframe) as input for training the classification algorithms SVM,KNN, Decision Tree. After training, we created classification report for all three models, and the KNN results are better than other two algorithms.

Now, using the KNN model, we gave annual_reports from validation folder of FNS2020, for testing. Before giving these reports for testing, first we have to do sentence tokenize, then preprocessing and feature extraction, now drop sentence, preprocessed_sentence within dataframe and give as input for testing. Results are generated consisting of predicitd_KNN_label.

using testing input file and the predicted file, both have file_name as common column,  Based on file_name as common column, we are merging input, predicted files,by this we have sentences along with predicted labels.

Now filter those sentences with KNN_predicted_label as 1 and generate summary.
