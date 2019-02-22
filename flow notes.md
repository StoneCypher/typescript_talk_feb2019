> Henlo, frens

switch to: dog picture



---

> I'm Dot Warner

switch to: dot warner picture



---

> As you know, I am an economist

switch to: dot warner as economist picture



---

> And that's probably good, because this is a talk about economics.

switch to: "Your Enemy, Typescript"

next tick adds: minions guy looking at easel in disbelief



---

> Let's talk about mistakes.

pause

next tick adds: > we all make them

next tick adds: > even topher

pause

next tick adds: > this talk wasn't one yet



---

Typescript in a nutshell

```typescript
let TheTemperature : Number;
```

`<@Typescript>` Okay


```typescript
TheTemperature = 'September';
```

`<@Typescript>` No


[[ Possibly phrase this as a row-flipped drake meme? ]]
[[ but also i'm tired of that meme ]]



---

Did you know:

next tick adds: This is what everyone thinks Typescript is

next tick adds: TheMoreYouKnow.jpg



---

Why do you `lint`?

next tick adds: * Because it saves us from mistakes

next tick adds: * ... sometimes embarrassing mistakes

next tick adds: * Because it is quick and easy

next tick adds: * Because it mostly does not require code changes

next tick adds: * Because everyone else who uses it suddenly insists

next tick adds: * Because people like fancy stuff

pause

next tick adds: Typescript shares these advantages.



---

Why do you `unit test`?

next tick adds: * Because it saves us from mistakes

next tick adds: * Because it results in more trustworthy code

next tick adds: * Because the work required pays out

next tick adds: * Because it provides a form of enforced documentation

next tick adds: * Because people like fancy stuff

pause

next tick adds: Typescript shares these advantages.



---

> Yeah, but it's just numbers to strings

Lol no it's not



---

Typescript can find the bug.  Can you?

```typescript
const formatPrice = (num, symbol = "$") =>
  `${symbol}${num.toFixed(2)}`;

formatPrice("1234");
```



---

This needs no annotation at all.

The formatted price is a string.  In use, it's being treated like a number; strings don't have `.toFixed`.

```typescript
const formatPrice = (num, symbol = "$") =>
  `${symbol}${num.toFixed(2)}`;

formatPrice("1234");
```



---

Typescript can find the bug.  Can you?

```typescript
type month = 'January' | 'February' | 'March' | 'April' | 'May' | 'June' | 'July'
           | 'August' | 'September' | 'October' | 'November' | 'December';

const NoLeapYear_DayCount(WhichMonth: Month) {
  switch (WhichMonth) {

    case 'February'  : return 28;

    case 'April'     :
    case 'June'      :
    case 'September' :
    case 'November'  : return 30;

    case 'January'   :
    case 'March'     :
    case 'May'       :
    case 'August'    :
    case 'October'   :
    case 'December'  : return 31;

  }
}
```



---

lol there's three



---

1) That's not how you define a function

```typescript
const NoLeapYear_DayCount(WhichMonth: Month) {
```

should be

```typescript
function NoLeapYear_DayCount(WhichMonth: Month) {
```

or

```typescript
const NoLeapYear_DayCount = (WhichMonth: Month) => {
```

---

Add a "never" to tell it it can't hit default, and it'll say
"wait, you didn't handle July"

```typescript
enum month { January, February, March, April, May, June, July,
             August, September, October, November, December };

const NoLeapYear_DayCount(WhichMonth: Month) {
  switch (WhichMonth) {

    case 'February  : return 28;
    case 'April     :
    case 'June      :
    case 'September :
    case 'November  : return 30;
    case 'January   :
    case 'March     :
    case 'May       :
    case 'August    :
    case 'October   :
    case 'December  : return 31;

    default:
      myDisallow: never = 'This should not be possible';

  }
}
```


---

No, but seriously

It actually is a talk on economics



---

Fact 1:

Programming costs time



---

Fact 2:

Your time costs money



---

Imperative: saving time saves money

You care about your time, and your boss cares about money

Some kind of incentives are aligned joke belongs here
