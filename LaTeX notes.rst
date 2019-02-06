RESOURCES
https://www.sharelatex.com -- builtin online environment!

SETUP
\documentclass[11pt,a4paper,landscape,twocolumn,twoside]{} article (this is the most common), book, letter, report, slides, beamer (for presentations)
\usepackage{packageyouwant} %comment. i suggest writing which functions from the package you intend on using here
\newcommand{\name}[number of arguments]{definition code} %this is how to define a macro
\newcommand{\comment}[1]{} %for example, this new command allows you to make inline comments
\newcommand{\em}[1]{\emph{#1}} % this command is a shorthand for emph.  It takes in the first parameter #1, and emphasizes it.
vdots
\begin{document}

LISTS
en.m.wikibooks.org/wiki/LaTeX/List_Structures

\begin{} itemize (ul), enumerate (ol), description
[label=override the label! use \alph, \roman, \arabic, and capitalize first letter if you want caps]
\item this is item 1
\item \hfill \\
this is item 2 which started right BELOW the label
\item \hline \\
this is the same but a line instead of blankness
\item[override this label only] this is item 4
\item[Term] description (this is what you do in description lists)
\end{}

TEXT
\text{} others are (two letter postfixes)...
\textbf - bold face
\textsc - small caps
\textsf - sansserif
\texttt - teletype
\emph to get italics

VARIABLES
greek variables are a high priority in latex, so all are simply their rightful names.  for variables with an alternate symbol, prefix with 'var' to get the alternate version.  Not all greek variables have a capital version.

COMPARISONS
= < > leq geq
\not= \not< \not> \not\leq \not\geq

OPERATIONS
pm mp cdot
cap cup
oplus ominus otimes oslash odot

DOTS
cdot cdots ldots vdots ddots

*use \displaystyle to force pretty display in inline sum, int, prod, etc

ARRAYS
MATRICES

MATH MISCELLANEOUS
\usepackage{fourier} % \widearc
\usepackage{amsmath} % \overleftrightarrow and many usefuls!
\usepackage{amssymb} % \therefore, \Bbbk, \smallsetminus, and other math particulars you might want


overbrace{content}^{and text above is useful}
underbrace "
overline underline overrightarrow overleftarrow

vec, hat

MISCELLANEOUS
You can write PHANTOM WHITESPACE like this: \hphantom{stuff}
usually, \, is 3px, \: is 4px, and \; is 5 px.
LaTeX is NOT whitespace insensitive.  For example, when you have embed tags such as $ ... $ or $$ ... $$, you cannot have a blank line between the begin tag and the first line of content.  Same for the end tag.
``this is how you double quote things'' like in man pages!
if necessary, use \! negative space to overlap symbols together.
macros are made like this: \newcommand{\subsetcirc}{\mathrel{\subset\!\!\!\!\!\circ}}
10, 11, and 12pt are the only font sizes you can have as documentclass.  Use tiny, scriptsize, footnotesize, small, normalsize, large, Large, LARGE, huge, Huge for things within document.

You can use mbox to maybe demathify stuff?  \\mathop{\\mbox{-}}   and you use mathop to make something a math operation! (puts a little buffer spacing on both sides, gives it quad width i think.)

\end{document}
