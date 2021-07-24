<div dir="rtl" style="padding:0 20% 0 20%">

# ברוכים הבאים ל Vue.js <img src="Vue.js_Logo.png" width="50" height="43.3" alt="Vue.js Logo">


## מבוא

**Vue.js (או בקיצור - Vue) היא ספריית javascript מתקדמת שעוזרת לנו ליצור SPA (Single Page Application) בצד הלקוח.**

מטרת המעבדה הנוכחית היא **להכיר, ללמוד ולהתנסות ב Vue.js** בפעם הראשונה וליצור **עמוד Register**.

לעומת עבודה 2, שבה יצרתם עמוד Register באמצעות שימוש בjavascript בסיסי ובספרייה JQuery, כעת אנחנו ניעזר ביכולת של Vue.js בנוסף לjavascript הבסיסי.

(דף Login יהיה בנוי בצורה דומה. אתם מוזמנים ליצור אותו בעצמכם לאחר מכן ולבדוק שהצלחתם)

## הכנה

1. להוריד את כלי הפיתוח עבור vue בתוך הדפדפן:
   - [עבור הדפדפן של Chrome](https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd)
   - [עבור הדפדפן של Firefox](https://addons.mozilla.org/en-US/firefox/addon/vue-js-devtools/)
2. לייבא את הקוד [מgithub](https://github.com/SISE-Web-Development-Environments/LAB10)
3. להוריד את התוספים הבאים לvscode:
   - Markdown All in One
   - Live Server
4. לפתוח את [הדוקומנטציה של Vue](https://vuejs.org/v2/guide/)

> _בזמנכם הפנוי לראות את [הדוקומנטציה של Vue](https://www.youtube.com/watch?v=OrxmtDw4pVI)_

## צורת הייבוא של Vue

את Vue אנחנו יכולים לייבא בכמה דרכים.\
במעבדה הזאת נייבא את Vue על ידי תג script (מומלץ להכריז עליו בhead):

<div id="import" dir="ltr" style="padding-left:15%;">

```html
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
```

</div>

> אפשר לראות שזה דומה לצורה בא ייבאנו את ספריית JQuery ש Vue באה להחליף.

## המבנה הבסיסי של קובץ המכיל קוד Vue

כל קובץ המכיל קוד Vue מורכב משלושה חלקים- 
  
1. HTML- קוד הHTML עם כל האלמנטים שיוצגו באתר שלנו.
2. Script- בחלק זה יופיע אובייקט הVue  אשר ישפיע וישלוט על האלמנטים המופיעים בחלק הראשון. 
3. Style - בחלק זה יופיעו חוקי CSS כפי שלמדנו, והם ישפיעו על הנראות של החלקים שנמצאים בחלק הראשון. 

דוגמה לחלוקה הבסיסית: 
```html
<!DOCTYPE html>
<!-- The View -->
<html>
  <head>
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
  </head>

  <body>
      ....
  </body>
</html>

<!-- The Logic -->
<script>
  // The Vue instance
</script>

<!-- The Style -->
<style></style>
```

## אובייקט Vue

כאשר אנחנו רוצים ליצור **אובייקט Vue** חדש, נרשום בקוד javascript:

<div id="new" dir="ltr" style="padding-left:15%;">

```javascript
var vm = new Vue({
  // properties
});
```

</div>

זוהי בעצם קריאה למופע של אובייקט Vue, אשר מהווה בעצם את הroot instance של האפליקציה, מהאובייקט הזה האפליקציה תתחיל והאובייקט הזה גם יכיל את כל הקומפוננטות של האתר שלנו (נלמד על קומפוננטות בתרגולים הבאים). 

## element selector

ה-property הראשון של הvue instance  שעליו נדבר הוא el property. 
מטרת ה-el property היא לקשר בין הvue  לבין אחד האלמנטים הנמצאים ב-DOM. לאחר שהגדרנו את קישור זה- האלמנט המקושר ב-DOM יושפע מקוד הVue שלנו. 
 כלומר, הVue instance יאזין לאירועים ויוכל לבצע שינויים בtemplate אליו הוא מקושר. 

קובץ הHTML שבו משולב אובייקט הVue יראה כך:

<div dir="ltr" style="padding-left:15%;">

```html
<!DOCTYPE html>
<!-- The View -->
<html>
  <head>
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
  </head>

  <body>
    <!-- The Template -->
    <div id="template">
      hello world vue
    </div>
  </body>
</html>

<!-- The Logic -->
<script>
  // The Vue instance
  var vm = new Vue({
    el: "#template"
  });
</script>

<!-- The Style -->
<style></style>
```

</div>

**[קישור לדוגמאת הקוד הראשונה](examples/1_hello_world_vue.html)**

## <span id="task1" style="color:green;"> <-- משימה 1 --> </span>

**בקובץ [register.html](task/register.html) (כרגע ריק) יש ליצור את השלד של המסמך.**

**בדוגמא מעל ראינו שהשלד מורכב משלושה חלקים -**

1. **התצוגה - תחת תג HTML, שתייבא את Vue בhead ובbody תכיל אלמנט (לדוגמא div) שיהיה הtemplate של אובייקט הVue**

2. **הלוגיקה - תחת תג script, שתיצור אובייקט Vue המקושר לאלמנט שיצרתם ב (1)**
3. **עיצוב - (אופציונלי) תג style, שבתוכו נציין את העיצוב של המסמך שלנו**

_קישור למשימה [1](#task1) [2](#task2) [3](#task3) [4](#task4) [5](#task5) [6](#task6) [7](#task7)_



## data

ה-property הבא של אובייקט הVue עליו נדבר הוא data. בdata אנחנו מגדירים את כל המידע שהאובייקט מחזיק, כלומר כל השדות של האובייקט ותפקיד הdata property הוא לחבר בין המידע שמכיל האובייקט למידע שמוצג בtemplate. 
 שימו לב: כל המשתנים **חייבים** להיות מאותחלים באזור של הdata. 
<div dir="ltr" style="padding-left:15%;">

```javascript
data() {
  return {
    message: "Hello Vue!"
  };
}
```

</div>

כל הפרמטרים שחוזרים מdata נוספים כפרמטרים של האובייקט, והפנייה אליהם בתוך האובייקט היא כמו במחלקה בjava - דרך הפוינטר this.

<div dir="ltr" style="padding-left:15%;">

```javascript
this.message;
```

</div>

כאשר הערכים של אותם פרמטרים משתנים, התצוגה תגיב ותתעדכן לפי הערכים החדשים.

אחת האפשרויות לתצוגה של אותם ערכים ניתנת באמצעות שימוש בסוגריים מסולסלים ובתוכם שם הפרמטר:

<div dir="ltr" style="padding-left:15%;">

```html
{{ message }}
```

</div>

**[קישור לדוגמאת הקוד השנייה](examples/2_vue_object_properties.html)**

## <span id="task2" style="color:green;"> <-- משימה 2 --> </span>

**בקובץ [register.html](task/register.html) יש להגדיר משתנים שיחזיקו לנו את קלטי המשתמש של הform. את המשתנים האלה יש לרשום בתוך הdata כמו message בדוגמא למעלה.**

<div dir="ltr"">

```
username: "",
first_name: "",
last_name: "",
country: "",
password: "",
confirmation_password: "",
email: "",
profile_image_url: ""
```

</div>

_קישור למשימה [1](#task1) [2](#task2) [3](#task3) [4](#task4) [5](#task5) [6](#task6) [7](#task7)_

## methods


כל הפונקציות שבתוך methods נוספות כפונקציות של האובייקט, והפנייה אליהם בתוך האובייקט היא דרך הפוינטר this.

<div dir="ltr" style="padding-left:15%;">

```javascript
methods: {
  plus: function () {
    this.message += " And ";
    console.log(this.message);
  }
}
```

</div>


<div dir="ltr" style="padding-left:15%;">

```javascript
this.plus();
```

</div>

הפנייה לפונקציה מתוך התצוגה תהיה מתוך expression שנרשום באחד הdirectives.
ה-directives הן פקודות שמורות של Vue שנועדו לחסוך לנו קוד (מייצגות במילה אחת הרבה קוד שכבר ממומש) ולקשר את הtemplate ל-vue, לדוגמה באמצעות העברת אירועים. 


_**דוגמא:**_ קיים  directive בשם [v-on](#v-on) שמטרתו היא להגדיר event handler לאלמנטים בDOM, כלומר מה יקרה כאשר יתבצע אירוע מסויים לאלמנט מסויים. 
דוגמה לשימוש בv-on- 

<div dir="ltr" style="padding-left:15%;">

```html
<button v-on:click="plus">plus button</button>
```

</div>
כלומר, כאשר המשתמש ילחץ על הכתפור תופעל הפונקציה plus אשר מוגדרת בVue instance. 


**[קישור לדוגמאת הקוד השנייה](examples/2_vue_object_properties.html)**

## <span id="task3" style="color:green;"> <-- משימה 3 --> </span>

**בקובץ [register.html](task/register.html) יש ליצור:**

1. **אלמנט form שלו נגדיר את v-on בצורה הבאה:**

<div dir="ltr" style="padding-left:15%;">

```html
<form v-on:submit="handleRegister">
  ...
</form>
```

</div>

2. **אלמנט input מסוג <input type="submit" value="Submit">**
3. **פונקציה בתוך הפרמטר methods שתקרא בעת לחיצה על הכפתור. אתם יכולים לאתחל את הפונקציה שתעשה alert למחרוזת מסוימת.**

> **_הערה:_**

כאשר לוחצים על submit בform, הevent שיופעל הוא submit של האלמנט form.\
במקרה שלנו, הפונקציה handleRegister תופעל, אך לאחר סיומה תופעל גם הפונקציה הדיפולטית של אלמנט הform.\
בשביל למנוע את זה נוכל:

- להשתמש בתוך handleRegister ב: `event.preventDefault();`
- לציין prevent לצד הפעולה: `v-on:submit.prevent`

_קישור למשימה [1](#task1) [2](#task2) [3](#task3) [4](#task4) [5](#task5) [6](#task6) [7](#task7)_



---


 ## <div id="computed_with_setter">computed</div>

נשתמש בcomputed כאשר נרצה לעשות מניפולציותכלשהן או ליצור מידע חדש ממידע שכבר קיים (לדוגמה פילטריםעל רשימות, היפוך מחרוזות,שרשורים...) נשתמש בהם כמו getters. 
<div dir="ltr" style="padding-left:15%;">

```javascript
computed: {
  fullName: {
    // getter
    get: function () {
      return this.firstName + ' ' + this.lastName
    },
    // setter
    set: function (newValue) {
      var names = newValue.split(' ')
      this.firstName = names[0]
      this.lastName = names[names.length - 1]
    }
  }
}
```

</div>

עבור fullName, שכאשר נריץ:

<div dir="ltr" style="padding-left:15%;">

```javascript
this.fullName = "John Doe";
```

</div>
firstName ו lastName יתעדכנו ב John ו Doe בהתאמה

---



## directives

**סימונים על אלמנט DOM שבאמצעותם Vue מחבר התנהגות מסוימת לאלמנט.**

לרוב הסימונים האלה בVue יתחילו ב **-v**.

היום במעבדה נדבר על directives מפורסמים שגם נעשה בהם שימוש במעבדה.


ההתנהגות יכולה להיות:

- פעולה שתופעל ברגע שevent מסוים יתקיים
- קישור בין ערך של element לפרמטר של האובייקט- כשאחד מהם ישתנה אז כך גם השני. 
- הופעה והסתרה של אלמנטים בהתאם לקיום של תנאי מסויים. 

 ## <div id="v-on">v-on</div>

<div dir="ltr" style="padding-left:15%;">

Inside template:

```html
<button v-on:click="handleClick">
  Click me!
</button>
```

Inside Vue Object:

```javascript
methods: {
  handleClick: function() {
    alert('Clicked');
  }
}
```

</div>

**מאפשר לצרף לאלמנט פעולה שתופעל כאשר event קורה.**

> אותה פעולה נקראת event handler.

צורת הכתיבה תיהיה:

<div dir="ltr" style="padding-left:15%;">

```
v-on:EventName="Function | Inline Statement | Object"
```

</div>

בצורה מקוצרת במקום לרשום **:v-on** , נרשום **@**

<div dir="ltr" style="padding-left:15%;">

```html
<a @click="handleClick">Click me!</a>
```

</div>

> טיפ: באנגלית קוראים לסימן @ = at, אז אפשר לזכור את זה כ - at EventName, do somthing

**[קישור לדוגמאת הקוד השלישית](examples/3_data_bindings.html)**

[עוד על v-on](https://vuejs.org/v2/api/#v-on)

## <span id="task4" style="color:green;"> <-- משימה 4 - _רשות_ --> </span>

> **תזכורת: כאשר יצרנו את הכפתור submit השתמשנו בv-on.**

**כעת ב[register.html](task/register.html) אתם יכולים להוריד את :v-on ולהשאיר רק את @ כמו שראינו בדוגמא למעלה**

_קישור למשימה [1](#task1) [2](#task2) [3](#task3) [4](#task4) [5](#task5) [6](#task6) [7](#task7)_

## v-model

<div dir="ltr" style="padding-left:15%;">

Inside template:

```html
<input v-model="message" />
```

Inside Vue Object:

```javascript
data(){
  return {
    message: ""
  };
}
```

</div>

**מאפשר לנו ליצור two-way binding בין משתנה של אובייקט Vue לאלמנטי input.**

אלמנטי input שקיימים בhtml הם:

- input
- select
- textarea

> מאחורי הקלעים, v-model משתמש בv-on לevent של קלט עבור אלמנטיי input

צורת הכתיבה תיהיה:

<div dir="ltr" style="padding-left:15%;">

```
v-model="variable"
```

</div>

**[קישור לדוגמאת הקוד השלישית](examples/3_data_bindings.html)**

[עוד על v-model](https://vuejs.org/v2/api/#v-model)

## <span id="task5" style="color:green;"> <-- משימה 5 --> </span>

**בקובץ [register.html](task/register.html) יש ליצור את כל התגים הדרושים בתוך תג הform ולקשר אותם למשתנים שהגדרתם ב[משימה 2](#task2)**

<div dir="ltr">

```
* username - type=input.text
* first_name - type=input.text
* last_name - type=input.text
* country - type=select (you can start with a simple input.text)
* password - type=input.password
* confirmation_password - type=input.password
* email - type=input.email
* profile_page_url - type=input.text
```

</div>

_קישור למשימה [1](#task1) [2](#task2) [3](#task3) [4](#task4) [5](#task5) [6](#task6) [7](#task7)_

## v-if (and) v-else (and) v-else-if

<div dir="ltr" style="padding-left:15%;">

Inside template:

```html
<div v-if="flag">
  Good
</div>
<div v-else-if="flag2">
  Maybe Good
</div>
<div v-else>
  Not Good
</div>
```

Inside Vue Object:

```javascript
data(){
  return {
    flag: false,
    flag2: true
  };
}
```

</div>

**מאפשר לנו להציג ולהסתיר אלמנטים בהתבסס על קיום של תנאי כלשהו .**

האלמנטים יווצרו וימחקו מהDom בהתאם לתנאי.

**תהליך זה נעשה באופן דינאמי בהתאם לתנאי**, כלומר, ברגע שתוצאת התנאי משתנה, האלמנט ימחק/יתווסף לDom.

> v-else ו v-else-if בעלות אותו הגיון כמו בשאר שפות תכנות בכך שelse או else-if יופיע רק לאחר if.

צורת הכתיבה תיהיה:

<div dir="ltr" style="padding-left:15%;">

```
v-if="expression"
v-else-if="expression"
v-else
```

</div>

**[קישור לדוגמאת הקוד הרביעית](examples/4_conditions.html)**

[עוד על v-if](https://vuejs.org/v2/api/#v-if)\
[עוד על v-else](https://vuejs.org/v2/api/#v-else)\
[עוד על v-else-if](https://vuejs.org/v2/api/#v-else-if)

## <span id="task6" style="color:green;"> <-- משימה 6 --> </span>

**בקובץ [register.html](task/register.html) יש ליצור:**

1. **משתנה של שגיאות**

2. **בפונקציה שמטפלת בsubmit יש להוסיף בדיקות ובמידה ובדיקה יצאה שגויה יש להוסיף אותה למשתנה השגיאות.**\
    **הבדיקות יהיו:**

   > - **שם משתמש יהיה באורך בין 3 ל- 8 תווים (בעבודה יש להוסיף בדיקת הכלה של אותיות בלבד)**
   > - **אורך הסיסמה יהיה בין 5 ל-10 תוים**


3. **תג div שמציג את השגיאות אם הsubmit לא עבר בהצלחה ונתקל בשגיאות**

4. **תג div שמציג הודעת הצלחה - "ההרשמה האחרונה שלך עברה בהצלחה" במקרה והsubmit קרה בלי שגיאות**

_קישור למשימה [1](#task1) [2](#task2) [3](#task3) [4](#task4) [5](#task5) [6](#task6) [7](#task7)_

## v-for

<div dir="ltr" style="padding-left:15%;">

inside template:

```html
<div v-for="m in messages">
  {{ m }}
</div>
```

inside Vue Object:

```javascript
data(){
  return {
    messages: ["a", "b", "c"]
  };
}
```

</div>

מאפשר לנו לשכפל אלמנט מספר פעמים על פי קלט איטרטיבי (במקרה שלנו messages) כך שהtemplate שלהם זהה, אך הdata שלהם משתנה (לכל אחד message יהיה אחר)

<!-- בתוך כל אלמנט אנחנו יכולים לפנות למשתנה של האיטרציה (במקרה שלנו message). -->

לדוגמא, אם נרצה להציג רשימה, איך צורך לכתוב עבור כל אלמנט ברשימה תגיות \<li\>, נוכל לעשות זאת בקלות על ידי ריצה על איברי הרשימה ושימוש בv-for

נוכל לרשום את זה בפסאודו קוד בצורה כזאת:

<div dir="ltr" style="padding-left:15%;">

```javascript
for item in Iterable:
  CreateDomElement(Element, item)
```

</div>

צורת הכתיבה תיהיה:

<div dir="ltr" style="padding-left:15%;">

```
v-for="alias in Array | Object | number | string | Iterable"
```

</div>

> צורת הכתיבה חייבת להיות בצורה `alias in expression` , כדי לספק כינוי לאלמנט הנוכחי באיטרציה.

בנוסף, אפשר לציין כינוי לאינדקס (וגם למפתח אם עוברים על אובייקט):

<div dir="ltr" style="padding-left:15%;">

```
v-for="(item, index) in items"
v-for="(val, key) in object"
v-for="(val, name, index) in object"
```

</div>

<div dir="ltr" style="padding-left:15%;">

Inside template:

```html
<div v-for="(message, i) in messages">
  {{ i }}) {{ message }}
</div>

<ol>
  <li v-for="message in messages">
    {{ message }}
  </li>
</ol>
```

Inside Vue Object:

```javascript
data(){
  return {
    messages: [
      "Eran: hey! 😁",
      "Yossi: hey! whats up? 🤷‍♂️",
      "Eran: i'm good ✌"
    ]
  };
}
```

</div>

כברירת מחדל vue מנסה לעשות מינימום שינויים בDom.\
אם סדר האלמנטים שיצרנו חשוב, ואנו רוצים כי בעת שינוי ברשימה/אובייקט גם התצוגה תתעדכן, עלינו להוסיף לכל אלמנט **key (מזהה) ייחודי**.

את הkey נקח מתוך הפרמטרים של המשתנה.

**_לדוגמא_**, אם נקח את הדוגמא ממקודם, מה שיכול להיות ייחודי עבור הודעה היא הזמן שבו היא נשלחה (הסדר יכול להשתנות כי יכולה להיות אפשרות למחוק הודעות).\
לכן אם נשמור את ההודעות בצורה הבאה:

<div dir="ltr" style="padding-left:15%;">

Inside Vue Object:

```javascript
data(){
  return {
    messages: [
      { time:1, sender:"Eran", message: "hey! 😁"},
      { time:2, sender:"Yossi", message: "hey! whats up? 🤷‍♂️"},
      { time:3, sender:"Eran", message: "i'm good ✌"}
    ]
  };
}
```

</div>

נוכל להגדיר את v-for בצורה הבאה:

<div dir="ltr" style="padding-left:15%;">

Inside template:

```html
<ol>
  <li v-for="message in messages" :key="message.time">
    {{ message.sender }}: {{message.message}} (time={{message.time}})
  </li>
</ol>
```

</div>

**[קישור לדוגמאת הקוד החמישית](examples/5_loops.html)**

[עוד על v-for](https://vuejs.org/v2/api/#v-for)

## <span id="task7" style="color:green;"> <-- משימה 7 --> </span>

**יש לשנות את התצוגה של השגיאות לתצוגה שמשתמשת בv-for**

_קישור למשימה [1](#task1) [2](#task2) [3](#task3) [4](#task4) [5](#task5) [6](#task6) [7](#task7)_

## form in Vue

בעזרת כל מה שלמדנו עד עכשיו נוכל לראות שיצרנו form element שבזמן submit יעשה ואלידציה לקלט.\
אם הקלט לא עבר את הואלידציה, נציג למשתמש מה הטעויות שלו.

במידה וכל הקלט תקין, נוכל להוסיף באמצעות axios שליחה של בקשה עם כל הנתונים ששמרנו.

קישור לקוד של שרת [אפשר למצוא פה](https://github.com/SISE-Web-Development-Environments/LAB10_SERVER)

**[קישור לדוגמאת הקוד השישית](examples/6_form.html)**

[מידע על שימוש בform inputs ב Vue](https://vuejs.org/v2/guide/forms.html)\
[מידע על form validations ב Vue](https://vuejs.org/v2/guide/forms.html)

&nbsp;
&nbsp;

## העברת בקשות לשרת 

את כל הבקשות שנרצה לשלוח לשרת נשלח באמצעות ספריית axios. 
הבקשה לשרת תהיה ל-endpoint מסויים של השרת, היא תהיה כתובה בתוך methods בצורה הבאה: 

<div dir="ltr" style="padding-left:15%;">

```javascript
      async Register() {
      try {
        const response = await this.axios.post(
          this.server_url + "/register", 
          {
            username: this.form.username,
            firstName: this.form.firstName,
            lastName: this.form.lastName,
            country: this.form.country,
          }
        );
      } catch (err) {
        this.form.submitError = err.response.data.message;
        this.form.username = "";
        }
      }
```
</div>

