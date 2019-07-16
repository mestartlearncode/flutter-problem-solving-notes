# flutter-problem-solving-notes
a collection of flutter coding problem and its solution

<h2>#case 1 - Cant call async function on init state</h2>

sometime we need to call `async function` on init state of stateful widget, for example: "we need to get saved value that store at storage / `SharedPreferences` and pointing it to **Radio Button** choice list"

if we call `async function` directly, we will get error message : 
>**await expression can only be used in an asynchronous function**

**Solution:**

use `then()` if you want to execute `async function` in init state :

    String pickRadioValue;
      @override
        void initState() {
          setState(() {
            ads.getPreferredLanguage().then((result){
              setState(() {
                print (":: debug result >>>"+result.toString());
                pickRadioValue = result;
              });
            });
          });
          super.initState();
    }

