all: time_duhamel time_mayer time_r_mayer test_mayer test_duhamel



time_duhamel: time_duhamel.c fft_duhamel.c
 cc -O4 -o time_duhamel time_duhamel.c fft_duhamel.c -lm

time_mayer: time_mayer.c fft_mayer.c
 cc -O4 -o time_mayer time_mayer.c fft_mayer.c

time_r_mayer: time_r_mayer.c fft_mayer.c
 cc -O4 -o time_r_mayer time_r_mayer.c fft_mayer.c



test_duhamel: test_duhamel.c fft_duhamel.c
 cc -O4 -o test_duhamel test_duhamel.c fft_duhamel.c -lm

test_mayer: test_mayer.c fft_mayer.c
 cc -O4 -o test_mayer test_mayer.c fft_mayer.c

