CSE 542 Fall 2024 Lab 2

## Basic Information about Project

* Group member:
Qinzhou Song qinzhounick@wustl.edu
Sicheng Yang sicheng@wustl.edu

* Program Design
This program will loop through all the scene and print the speakers' saying with enter and exit information. we
develop this progream using a module lab2. We divide the role into detailed pieces and make them seperate Structs
like Play and Player etc. However, to make the use of program easier in the future, we simplify the call to play() and
recite() and the entire program will run.

* Observations:
This assignment was confusing while we were changing the original play.rs and player.rs, but when we got to the scene_fragments.rs,
  it all made sense. It was hard to implement the player speaking order without a bigger scope of knowing how the entire scene get printed out.
The instructions were as detailed as lab1, which gave us flexibility on design choices. 
We do appreciate that as it grants more satisfaction after we printed out the entire scene.

## Detailed Instruction
* Modules:
We added declarations and script_gen into our mod.rs and then we added use statement like use lab2::declarations
  to use the public types, constants, and functions in main.rs.
We changed the print statements under whinge mode so that they only print to the standard error stream.
We had challenges where our script_gen function was private and cannot be used in main.rs so we made it a public function.
We also had error from not including the atomic library in the script_gen file so we added that.

* Structs:
We declared structs for Play with title and a vector of players and Player with PlayLines, name, and index. 
  We mainly had problem with the recite function in Play, because the lines are now in seperate structs 
  and we cannot sort all the lines at the same time. 
We changed the recite function so that we had an universal order number that tracks the current line number,
  then, we loop through all the players that still has remainning lines, if we found the line number, print it out,
  if not, we skip the line number, if whinge is set, we complain about missing lines number, and go to the next one.

* Return Wrapper:
We implement return wrapper that can auto encapsulate error and normal return to make main easy. In this code, we face import issue and solve this by adding use statements

* Scene Fragments:
We deal with differents fragments by calling enter, recite, and exit multiple times in play. When we wrote the enter and exit, the order of speaker is wrong, and we change it by using rev() methods. We also face communication issue in collaboration but fix at the end.

* Testing:
1. Normal without whinge mode:
[sicheng@iht32-1502.sif lab2]$ ./main normal.txt
Hamlet Prince of Denmark ACT II Scene I A room in Polonius house by William Shakespeare 
[Enter Polonius.]
[Enter Reynaldo.]

Polonius
Give him this money and these notes, Reynaldo.

Reynaldo
I will, my lord.

Polonius
You shall do marvellous wisely, good Reynaldo,
Before You visit him, to make inquiry
Of his behaviour.

Reynaldo
My lord, I did intend it.

Polonius
Marry, well said; very well said. Look you, sir,
Enquire me first what Danskers are in Paris;
And how, and who, what means, and where they keep,
What company, at what expense; and finding,
By this encompassment and drift of question,
That they do know my son, come you more nearer
Than your particular demands will touch it:
Take you, as 'twere, some distant knowledge of him;
As thus, 'I know his father and his friends,
And in part hi;m;--do you mark this, Reynaldo?

Reynaldo
Ay, very well, my lord.

Polonius
'And in part him;--but,' you may say, 'not well:
But if't be he I mean, he's very wild;
Addicted so and so;' and there put on him
What forgeries you please; marry, none so rank
As may dishonour him; take heed of that;
But, sir, such wanton, wild, and usual slips
As are companions noted and most known
To youth and liberty.

Reynaldo
As gaming, my lord.

Polonius
Ay, or drinking, fencing, swearing, quarrelling,
Drabbing:--you may go so far.

Reynaldo
My lord, that would dishonour him.

Polonius
Faith, no; as you may season it in the charge.
You must not put another scandal on him,
That he is open to incontinency;
That's not my meaning: but breathe his faults so quaintly
That they may seem the taints of liberty;
The flash and outbreak of a fiery mind;
A savageness in unreclaimed blood,
Of general assault.

Reynaldo
But, my good lord,--

Polonius
Wherefore should you do this?

Reynaldo
Ay, my lord,
I would know that.

Polonius
Marry, sir, here's my drift;
And I believe it is a fetch of warrant:
You laying these slight sullies on my son
As 'twere a thing a little soil'd i' the working,
Mark you,
Your party in converse, him you would sound,
Having ever seen in the prenominate crimes
The youth you breathe of guilty, be assur'd
He closes with you in this consequence;
'Good sir,' or so; or 'friend,' or 'gentleman'--
According to the phrase or the addition
Of man and country.

Reynaldo
Very good, my lord.

Polonius
And then, sir, does he this,--he does--What was I about to say?--
By the mass, I was about to say something:--Where did I leave?

Reynaldo
At 'closes in the consequence,' at 'friend or so,' and
gentleman.'

Polonius
At--closes in the consequence'--ay, marry!
He closes with you thus:--'I know the gentleman;
I saw him yesterday, or t'other day,
Or then, or then; with such, or such; and, as you say,
There was he gaming; there o'ertook in's rouse;
There falling out at tennis': or perchance,
'I saw him enter such a house of sale,'--
Videlicet, a brothel,--or so forth.--
See you now;
Your bait of falsehood takes this carp of truth:
And thus do we of wisdom and of reach,
With windlaces, and with assays of bias,
By indirections find directions out:
So, by my former lecture and advice,
Shall you my son. You have me, have you not?

Reynaldo
My lord, I have.

Polonius
God b' wi' you, fare you well.

Reynaldo
Good my lord!

Polonius
Observe his inclination in yourself.

Reynaldo
I shall, my lord.

Polonius
And let him ply his music.

Reynaldo
Well, my lord.

Polonius
Farewell!

[Exit Reynaldo.]
[Enter Ophelia.]

Polonius
How now, Ophelia! what's the matter?

Ophelia
Alas, my lord, I have been so affrighted!

Polonius
With what, i' the name of God?

Ophelia
My lord, as I was sewing in my chamber,
Lord Hamlet,--with his doublet all unbrac'd;
No hat upon his head; his stockings foul'd,
Ungart'red, and down-gyved to his ankle;
Pale as his shirt; his knees knocking each other;
And with a look so piteous in purport
As if he had been loosed out of hell
To speak of horrors,--he comes before me.

Polonius
Mad for thy love?

Ophelia
My lord, I do not know;
But truly I do fear it.

Polonius
What said he?

Ophelia
He took me by the wrist, and held me hard;
Then goes he to the length of all his arm;
And with his other hand thus o'er his brow,
He falls to such perusal of my face
As he would draw it. Long stay'd he so;
At last,--a little shaking of mine arm,
And thrice his head thus waving up and down,--
He rais'd a sigh so piteous and profound
As it did seem to shatter all his bulk
And end his being: that done, he lets me go:
And, with his head over his shoulder turn'd
He seem'd to find his way without his eyes;
For out o' doors he went without their help,
And to the last bended their light on me.

Polonius
Come, go with me: I will go seek the king.
This is the very ecstasy of love;
Whose violent property fordoes itself,
And leads the will to desperate undertakings,
As oft as any passion under heaven
That does afflict our natures. I am sorry,--
What, have you given him any hard words of late?

Ophelia
No, my good lord; but, as you did command,
I did repel his letters and denied
His access to me.

Polonius
That hath made him mad.
I am sorry that with better heed and judgment
I had not quoted him: I fear'd he did but trifle,
And meant to wreck thee; but beshrew my jealousy!
It seems it as proper to our age
To cast beyond ourselves in our opinions
As it is common for the younger sort
To lack discretion. Come, go we to the king:
This must be known; which, being kept close, might move
More grief to hide than hate to utter love.

[Exit Ophelia.]
[Exit Polonius.]

Hamlet Prince of Denmark ACT II Scene II A room in the Castle by William Shakespeare 
[Enter King.]
[Enter Queen.]
[Enter Rosencrantz.]
[Enter Guildenstern.]

King
Welcome, dear Rosencrantz and Guildenstern!
Moreover that we much did long to see you,
The need we have to use you did provoke
Our hasty sending. Something have you heard
Of Hamlet's transformation; so I call it,
Since nor the exterior nor the inward man
Resembles that it was. What it should be,
More than his father's death, that thus hath put him
So much from the understanding of himself,
I cannot dream of: I entreat you both
That, being of so young days brought up with him,
And since so neighbour'd to his youth and humour,
That you vouchsafe your rest here in our court
Some little time: so by your companies
To draw him on to pleasures, and to gather,
So much as from occasion you may glean,
Whether aught, to us unknown, afflicts him thus,
That, open'd, lies within our remedy.

Queen
Good gentlemen, he hath much talk'd of you,
And sure I am two men there are not living
To whom he more adheres. If it will please you
To show us so much gentry and good-will
As to expend your time with us awhile,
For the supply and profit of our hope,
Your visitation shall receive such thanks
As fits a king's remembrance.

Rosencrantz
Both your majesties
Might, by the sovereign power you have of us,
Put your dread pleasures more into command
Than to entreaty.

Guildenstern
We both obey,
And here give up ourselves, in the full bent,
To lay our service freely at your feet,
To be commanded.

King
Thanks, Rosencrantz and gentle Guildenstern.

Queen
Thanks, Guildenstern and gentle Rosencrantz:
And I beseech you instantly to visit
My too-much-changed son.--Go, some of you,
And bring these gentlemen where Hamlet is.

Guildenstern
Heavens make our presence and our practices
Pleasant and helpful to him!

Queen
Ay, amen!

[Exit Guildenstern.]
[Exit Rosencrantz.]
[Exit Queen.]
[Exit King.]

The program run successfully

2. File does not exist case
[sicheng@iht32-1502.sif lab2]$ ./main no.txt
no.txt is not a valid filename
Invalid file name: no.txt
Error: 2

3. File contains blank line
[sicheng@iht32-1502.sif lab2]$ ./main blank_line.txt 
** The ouput is the same as normal case

4. Extra argument in config
[sicheng@iht32-1502.sif lab2]$ ./main extra_token.txt
The output is the same as normal case

5. Whinge mode that complain about missing order
[sicheng@iht32-1502.sif lab2]$ ./main normal.txt whinge
... (long text omitted)
[Enter Guildenstern.]
Character line "0" missing
...

6. Whinge mode complains about duplicate order
[sicheng@iht32-1502.sif lab2]$ ./main duplicate.txt whinge
...
Character line "80" duplicate
...

7. No scene title with whinge
[sicheng@iht32-1502.sif lab2]$ ./main no_title.txt whinge
Config file line "[scene]" missing scene title
...

8. additional parameter with whinge mode
[sicheng@iht32-1502.sif lab2]$ ./main extra_token.txt whinge
Config file line "hamlet_ii_1a_config.txt extra" has extra tokens
...

9. extra command line argument
[sicheng@iht32-1502.sif lab2]$ ./main normal.txt whinge extra
usage: ./main <script_file_name> [whinge]
Error: 1

10. extra argument in config file
[sicheng@iht32-1502.sif lab2]$ ./main extra_config.txt whinge
Config file line "Polonius Polonius_hamlet_ii_1a.txt extra" length not equal to 2.
...

* How to unpack the program: download the lab.zip and unzip the package

* How to build the program:
1. Please put all the file under lab1 folder
2. use "rustc ./src/main.rs" to compile the program
3. you can use "./main <configuration file>" to ignore warning message or 
"./main <configuration file> whinge" to enable warning message. You can also use "cargo run <configuration file>"
or "cargo run <configuration file> whinge"
