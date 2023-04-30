Download Link: https://assignmentchef.com/product/solved-wod-workout-of-the-day
<br>
<a href="https://www.youtube.com/playlist?list=PLhOuww6rJJNM2jtyu3zw3aIeZ8Ov7hSy-" rel="nofollow">https://www.youtube.com/playlist?list=PLhOuww6rJJNM2jtyu3zw3aIeZ8Ov7hSy-</a>

Create a program that will read a CSV <code>-f</code> or <code>--file</code> of exercises (default <code>exercises.csv</code>) and create a Workout of the Day:

<pre><code>$ ./wod.pyExercise              Reps------------------  ------Pushups                 74Hand-stand pushups      10Squats                  29Burpees                 33</code></pre>

The program should accept an alternate <code>--file</code>:

<pre><code>$ ./wod.py -f silly-exercises.csvExercise                Reps--------------------  ------Erstwhile Lunges          18Hanging Chads             90Red Barchettas            36Masochistic Eardowns      29</code></pre>

And should reject non-existent file arguments:

<pre><code>$ ./wod.py -f lkjdflkjusage: wod.py [-h] [-f str] [-s int] [-n int] [-e]wod.py: error: argument -f/--file: can't open 'lkjdflkj': [Errno 2] No such file or directory: 'lkjdflkj'</code></pre>

The file structure looks like this:

<pre><code>$ cat exercises.csvexercise,repsBurpees,20-50Situps,40-100Pushups,25-75Squats,20-50Pullups,10-30Hand-stand pushups,5-20Lunges,20-40Plank,30-60Crunches,20-30</code></pre>

The program should accept an <code>-n</code> or <code>--num</code> argument to control the number of exercises which are randomly chosen from the input file. The “Reps” value will be randomly chosen from the given low/high range in the “reps” column:

<pre><code>$ ./wod.py -n 2Exercise      Reps----------  ------Situps          83Pullups         30</code></pre>

The program should accept a <code>-s</code> or <code>--seed</code> value for the random seed to ensure reproducibility:

<pre><code>$ ./wod.py -s 1Exercise      Reps----------  ------Pushups         56Situps          88Crunches        27Burpees         35</code></pre>

As well as a <code>-e</code> or <code>--easy</code> flag to indicate that the reps should be halved:

<pre><code>$ ./wod.py -s 1 -eExercise      Reps----------  ------Pushups         28Situps          44Crunches        13Burpees         17</code></pre>

The program should print a usage for the <code>-h</code> or <code>--help</code> flags:

<pre><code>$ ./wod.py -husage: wod.py [-h] [-f str] [-s int] [-n int] [-e]Create Workout Of (the) Day (WOD)optional arguments:  -h, --help          show this help message and exit  -f str, --file str  CSV input file of exercises (default: exercises.csv)  -s int, --seed int  Random seed (default: None)  -n int, --num int   Number of exercises (default: 4)  -e, --easy          Halve the reps (default: False)</code></pre>

Run the test suite to ensure your program is working correctly:

<pre><code>$ make testpytest -xv test.py============================= test session starts ==============================...collected 8 itemstest.py::test_exists PASSED                                              [ 12%]test.py::test_usage PASSED                                               [ 25%]test.py::test_bad_num PASSED                                             [ 37%]test.py::test_bad_file PASSED                                            [ 50%]test.py::test_seed1 PASSED                                               [ 62%]test.py::test_seed1_easy PASSED                                          [ 75%]test.py::test_seed2_num8 PASSED                                          [ 87%]test.py::test_seed4_num3_input2 PASSED                                   [100%]============================== 8 passed in 0.64s ===============================</code></pre>

The test suite only checks your program using well-formed input files. There are several “bad” input files provided which are not used by the test but are provided for you to try with your program. These represent several types of real-world problems you might encounter parsing delimited text files.