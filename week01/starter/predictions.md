| Step | Prediction: what will you see? | What you saw | Same? |
   |---|---|---|---|
   | a. Change `'Hello World!'` in `lib/main.dart` to a greeting in your language, then press `r` | the app will display `ሰላም` without restarting the app. | the app displayed the new greeting without restarting | yes |
   | b. Change `runApp(const MainApp())` to `runApp(const Placeholder())`, then press `r` | the app will display the same text | the previous greeting remained | yes |
   | c. With the change from b still there, press `R` | it will show a placeholder text | a large X shaped placeholder appeared on a white background | no |


## Task 5 — capitalizeWords

| Input | My prediction | Actual result | Correct? |
|---|---|---|---|
| 'addis ababa' | Addis Ababa | Addis Ababa | Yes |
| 'hello  world' | error | throws a RangeError | Yes |
| '' | '' | throws a RangeError | No |

### Mark- incorrect statement in the assistant's answer ###

1. Incorrect statement: the answer said that splitting the string with split(' ') ignores repeated spaces, so 'hello  world' works correctly. This is incorrect because the split(' ') separates string at every space. so 'hello  world' will result ['hello', '', 'world']. the empty string causes the function to fail  when it tries to access word[0]. i discovered this through testing.

2. Incorrect statement: the answer said the function handles all inputs safely. The function doesn't handle an empty string safely. when the input is '' splitting produces an empty word and accessing word[0] causes RangeError. i discovered it by testing it.


### The correct function ###


String capitalizeWords(String text) {
  if(text.trim().isEmpty){
    return '';
  }

  return text
      .trim()
      .split(' ')
      .where((word)=> word.isNotEmpty)
      .map((word) => word[0].toUpperCase() + word.substring(1))
      .join(' ');
}