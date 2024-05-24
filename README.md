Short Description of the Code


Download Video and Extract Audio: I used the pytube library to download the YouTube video because its a straightforward and reliable tool for accessing video content. For extracting the audio, pydub is very effective as it handles various audio formats and provides easy-to-use methods for exporting audio files.

Transcription of Audio To transcribe the audio, I chose the Wav2Vec2ForCTC model from Hugging Face. This model is well-regarded for its high accuracy in speech recognition tasks. I used it because it's pre-trained on a large dataset, which makes it highly effective at converting spoken language into text without needing additional training. By setting the audio sample rate to 16kHz and ensuring it is mono, I optimized the transcription quality.

Time-Align Transcript with Audio For aligning the transcript with the audio, I devised a method to calculate the average duration of each word. Although this method assumes a uniform distribution of words, it is straightforward and allows for a basic alignment without complex algorithms. This approach provides a quick and understandable way to match the text with the corresponding audio segments.

Semantic Chunking of Data I used the nltk library to split the transcription into sentences for semantic chunking. This library is well-suited for natural language processing tasks. By grouping sentences into chunks and ensuring each chunk is less than 15 seconds long, I maintained the semantic integrity of the text while also adhering to a manageable chunk length for analysis. This approach balances the need for meaningful text segments with practical audio chunk sizes.

Handling RAM Limitations Initially, I encountered a "ran out of RAM" error when processing the entire audio file at once. To overcome this, I modified the approach to process the audio in smaller chunks, specifically 60-second segments. This chunking method allowed me to handle the audio transcription without exceeding the memory limits of the environment. By processing each chunk individually and then combining the results, I managed to efficiently transcribe the entire audio while keeping the memory usage within acceptable limits.

# Utilizing Ground-Truth Transcripts
To improve the quality of the transcript, I would use a ground-truth transcript. We could compare the automatic transcription with this perfect version and use a method called dynamic time warping (DTW) to line up the words in both versions, which should help us see where the automatic transcription made mistakes. By looking at where the words don't match, wr can correct the errors in the automatic transcription by replacing the wrong words with the right ones from the ground-truth transcript. This way, the ground-truth transcript helps me make the automatic transcription much more accurate.
