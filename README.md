# Speech-to-Speech-Translation-with-Voice-Cloning
## Описание проблемы
Необходимо реализовать перевод русской речи в английскую с учетом голоса диктора.

Данная задача разбивается на несколько подзадач:
1. аудиозапись --> русская речь + фон
2. русская речь --> русский текст
3. русский текст --> английский текст
4. английский текст + русская речь --> английская речь

## Audio Preprocessing
В качестве препросессинга до подачи в ASR модель для решения проблемы галлюцинирования модели Whisper было сделано следующее:
1. Music Voice Separation - разделение аудиозаписи на отдельно дорожку речи и фона ([voice-remover](https://github.com/tsurumeso/vocal-remover))
2. Удаление тишины (ffmpeg)
3. Нормализация аудио по уровню громкости ([ffmpeg-normalize](https://github.com/slhck/ffmpeg-normalize))
4. Voice Activity Detection ([silero](https://github.com/snakers4/silero-vad))

Для разделения аудио на речь и фон, были рассмотрены три библиотеки: voice-remover, spleeter, librosa.
Ниже приведены результаты работы каждой из библиотек.

  <details>
  <summary><h4>original 15 seconds audio</h4></summary>

  https://github.com/Allessyer/Speech-to-Speech-Translation-with-Voice-Cloning/assets/71093827/9e379394-520d-4a29-9e6a-78710d7682f1
  </details>

  <details>
  <summary><h4>Librosa Voice Separator</h4></summary>
  <details>
  <summary><h5>vocal and background</h5></summary>

https://github.com/Allessyer/Speech-to-Speech-Translation-with-Voice-Cloning/assets/71093827/7104586b-653f-453d-a731-9a13d51d8161

https://github.com/Allessyer/Speech-to-Speech-Translation-with-Voice-Cloning/assets/71093827/5807b1dd-04a0-4e79-b006-fce8c8f9b254

  </details>
  </details>  

  <details>
  <summary><h4>Vocal-remover</h4></summary>
  <details>
  <summary><h5>vocal and background</h5></summary>


https://github.com/Allessyer/Speech-to-Speech-Translation-with-Voice-Cloning/assets/71093827/cfa8f340-6fd4-473a-a538-6d5be2a45f32

https://github.com/Allessyer/Speech-to-Speech-Translation-with-Voice-Cloning/assets/71093827/36fd53dc-b7e1-43f7-81d9-607561a0e8cd


  </details>
  </details>  
  
  <details>
  <summary><h4>Spleeter</h4></summary>

  <details>
  <summary><h5>vocal and background</h5></summary>
  
  https://github.com/Allessyer/Speech-to-Speech-Translation-with-Voice-Cloning/assets/71093827/5eded025-60a1-47f4-aed5-bb62068aff83
  
  https://github.com/Allessyer/Speech-to-Speech-Translation-with-Voice-Cloning/assets/71093827/5c49f0b7-2bae-4b29-9bf5-508fec6b33bf

  </details>
  </details>  

  ## ASR и перевод
  - ASR модель: [whisper-medium](https://huggingface.co/openai/whisper-medium)
  - Translation модель: [Helsinki-NLP/opus-mt-ru-en](https://huggingface.co/Helsinki-NLP/opus-mt-ru-en)

  ## TTS with voice cloning

  Три основные модели TTS и их результаты:

  <details>
  <summary><h4>original 7 seconds audio</h4></summary>

https://github.com/Allessyer/Speech-to-Speech-Translation-with-Voice-Cloning/assets/71093827/c6e612e0-0430-4561-a49a-c8204f7942e4

  </details>

  <details>
  <summary><h4>[bark](https://github.com/serp-ai/bark-with-voice-clone)</h4></summary>


https://github.com/Allessyer/Speech-to-Speech-Translation-with-Voice-Cloning/assets/71093827/95fa7d5c-44c1-4011-bf82-db4822ca133c


  </details>

  
  <details>
  <summary><h4>[RTVC](https://github.com/CorentinJ/Real-Time-Voice-Cloning/tree/master/synthesizer)</h4></summary>


https://github.com/Allessyer/Speech-to-Speech-Translation-with-Voice-Cloning/assets/71093827/cc1d2f91-76b3-49c5-b925-fedf1caa7ef9


  </details>
  
  <details>
  <summary><h4>[tortoise](https://github.com/neonbjb/tortoise-tts)</h4></summary>


https://github.com/Allessyer/Speech-to-Speech-Translation-with-Voice-Cloning/assets/71093827/ae96d2d5-51c6-48e6-9a67-c133e07b878a


  </details>



## Google Colab Notebook

You can access and run the project in Google Colab by clicking the badge below:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://drive.google.com/file/d/1PGA0Qqa4rJiJGa8dARLol_Dvg9hlR_aH/view?usp=sharing)
  
  







