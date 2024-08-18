# Convert English podcast to Ukranian

1. Get audio from YouTube

```
yt-dlp -x https://www.youtube.com/watch\?v\=72HgJQUMqsc
```

2. Convert .m4a to .wav 16kHz

```
ffmpeg -i input.m4a -acodec pcm_s16le -ac 1 -ar 16000 output.wav
```

3. Transcribe audio to text with whisper ai

[ggerganov/whisper.cpp](http://github.com/ggerganov/whisper.cpp)

4. Translate text to Ukranian

<https://chatgpt.com/>

5. Play read aloud Ukranian text

6. Get `curl` media request

add screenshot

7. Specify `format=mp3` in `curl` request

```
curl 'https://chatgpt.com/backend-api/synthesize?format=mp3&...
--output output.mp3
```

---


```
git clone
cd whisper.cpp
make
./main --output-file output.txt -f output.wav
```

Use flash attention for speed up (optional)
```
./main --output-file output.txt -f output.wav --flash-attn
```

Example output.txt

```
./main --output-txt ./SertoriusI.txt -f ~/tmp/ukranian-podcast/output.wav
error: input file not found './SertoriusI.txt'
whisper_init_from_file_with_params_no_state: loading model from 'models/ggml-base.en.bin'
whisper_init_with_params_no_state: use gpu    = 1
whisper_init_with_params_no_state: flash attn = 0
whisper_init_with_params_no_state: gpu_device = 0
whisper_init_with_params_no_state: dtw        = 0
whisper_model_load: loading model
...
whisper_model_load: model size    =  147.37 MB
whisper_backend_init_gpu: using Metal backend
ggml_metal_init: allocating
ggml_metal_init: found device: Apple M1 Pro
ggml_metal_init: picking default device: Apple M1 Pro
ggml_metal_init: using embedded metal library
ggml_metal_init: GPU name:   Apple M1 Pro
...
system_info: n_threads = 4 / 10 | AVX = 0 | AVX2 = 0 | AVX512 = 0 | FMA = 0 | NEON = 1 | ARM_FMA = 1 | METAL = 1 | F16C = 0 | FP16_VA = 1 | WASM_SIMD = 0 | BLAS = 1 | SSE3 = 0 | SSSE3 = 0 | VSX = 0 | CUDA = 0 | COREML = 0 | OPENVINO = 0 | CANN = 0

main: processing '/Users/gianpaj/tmp/ukranian-podcast/output.wav' (49984946 samples, 3124.1 sec), 4 threads, 1 processors, 5 beams + best of 5, lang = en, task = transcribe, timestamps = 1 ...


[00:00:00.000 --> 00:00:05.940]   When he was around 30 years old, Ludwig von Beethoven started to notice in his conversations
[00:00:05.940 --> 00:00:09.640]   that he was having trouble hearing people with deep voices.
...
output_txt: saving output to '/Users/gianpaj/tmp/ukranian-podcast/output.wav.txt'

whisper_print_timings:     load time =   118.25 ms
whisper_print_timings:     fallbacks =  17 p /   0 h
whisper_print_timings:      mel time =  1235.48 ms
whisper_print_timings:   sample time = 14857.05 ms / 56770 runs (    0.26 ms per run)
whisper_print_timings:   encode time =  9637.69 ms /   133 runs (   72.46 ms per run)
whisper_print_timings:   decode time =   561.47 ms /   178 runs (    3.15 ms per run)
whisper_print_timings:   batchd time = 64612.36 ms / 55844 runs (    1.16 ms per run)
whisper_print_timings:   prompt time =  2703.93 ms / 33348 runs (    0.08 ms per run)
whisper_print_timings:    total time = 93937.28 ms
ggml_metal_free: deallocating
```
