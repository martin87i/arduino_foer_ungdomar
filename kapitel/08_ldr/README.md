# 8. LDR

Under den här lektionen använder vi en ljusberoende motstånd, kallas LDR.

## 8.1 Uppgift

Bygg up:

 * en potmeter, på A0

Programmera:

 * en `const` variabel `potmeter_stift` på riktigt stift
 * att få värdet av potmetern med `analogRead`
 * att skriva värdet av potmetern till Serial Monitor
 * vänta 100 millisecond varje `loop`

\pagebreak

## 8.2 Lösning

![](08_potmeter.png)

```
const int potmeter_stift = A0;

void setup() 
{
  pinMode(potmeter_stift, INPUT);
  Serial.begin(9600);
}

void loop() 
{
  Serial.print(analogRead(potmeter_stift));
  delay(100);  
}
```

\pagebreak

## 8.3 Uppgift

Skriv om programmet litegrann för att ha en funktion som heter `visar_potmeter`.

`visar_potmeter` kan redan:

 * få värdet av potmetern med `analogRead`
 * skriva värdet av potmetern till Serial Monitor

Addera till `visar_potmeter`:

```
if (analogRead(potmeter_stift) < 512)
{
  Serial.print("Potmeter ar till vanster");
} 
else 
{
  Serial.print("Potmeter ar till hoger");
}
```

![Dator](EmojiComputer.png) | ![Smiley](EmojiSmiley.png)
:-------------:|:----------------------------------------: 
`<`|'mindre än'

![](EmojiBowtie.png) | `512` är bara i mitten från alla möjliga värden `analogRead` kan ger
:-------------:|:----------------------------------------: 

\pagebreak

## 8.4 Lösning

```
const int potmeter_stift = A0;

void setup() 
{
  pinMode(potmeter_stift, INPUT);
  Serial.begin(9600);
}

void loop() 
{
  visar_potmeter();
  delay(100);  
}

void visar_potmeter() 
{
  Serial.print(analogRead(potmeter_stift));
  if (analogRead(potmeter_stift) < 512)
  {
    Serial.print("Potmeter ar till vanster");
  } 
  else 
  {
    Serial.print("Potmeter ar till hoger");
  }
}
```

\pagebreak

## 8.5 Uppgift

Byt potmeter mot en LDR.
En LDR är ansluten på samma sätt som en knapp:

 * det första benet dras till 5V
 * det andra benet dras till ett motstand med 10 kOhm, som går till GND
 * det tredje benet går till A0
 
Kör programmet med samma kod.

Vilket värde har LDR om du blockerar ljuset med din hand?
Vilket värde har LDR om ljuset är helt på den?

\pagebreak

## 8.6 Lösning

![](08_ldr.png)

\pagebreak

## 8.7 Slutuppgift

Addera en LED på 13.

Om du håller din hand över LDRen:

  * ska LEDen lysa upp 
  * ska Serial monitor säga 'Det ar mörkt'

Om du inte håller din hand över LDRen:

  * ska LEDen vara släckt
  * ska Serial monitor säga 'Det ar ljust'

