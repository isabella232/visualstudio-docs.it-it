---
title: Usa caratteri jolly
ms.date: 03/26/2018
ms.topic: conceptual
f1_keywords:
- vsregularexpressionhelp
- vs.regularexpressionhelp
- vs.wildcardsbuilder
- vs.netregularexpressionhelp
- vs.wildcards
helpviewer_keywords:
- regular expressions [Visual Studio]
- regular expressions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 755554b73fc80df151550f36e1846e07db70bcd8
ms.sourcegitcommit: fe212f8960d7882a1b0fdae9e22f008996aacf3c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222739"
---
# <a name="use-regular-expressions-in-visual-studio"></a>Usare espressioni regolari in Visual Studio

Visual Studio usa le [espressioni regolari di .NET](/dotnet/standard/base-types/regular-expressions) per trovare e sostituire il testo.

## <a name="regular-expression-examples"></a>Esempi di espressioni regolari

La tabella seguente contiene alcuni caratteri, operatori, costrutti ed esempi di modelli di espressioni regolari. Per informazioni più complete, vedere [Linguaggio di espressioni regolari](/dotnet/standard/base-types/regular-expression-language-quick-reference).

|Scopo|Espressione|Esempio|
|-------------|----------------|-------------|
|Trovare la corrispondenza con qualsiasi carattere singolo (ad eccezione di un'interruzione di riga). Per altre informazioni, vedere [Qualsiasi carattere](/dotnet/standard/base-types/character-classes-in-regular-expressions#any-character-).|.|`a.o` trova "aro" in "around" e "abo" in "about", ma non "acro" in "across".|
|Trovare la corrispondenza con zero o più occorrenze dell'espressione precedente (trovare quanti più caratteri corrispondenti possibile). Per altre informazioni, vedere [Trova la corrispondenza zero o più volte](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-).|*|`a*r` trova "r" in "rack", "ar" in "ark" e "aar" in "aardvark"|
|Trovare la corrispondenza con qualsiasi carattere zero o più volte (carattere jolly \*)|.*|`c.*e` trova "cke" in "racket", "comme" in "comment" e "code" in "code"|
|Trovare la corrispondenza con una o più occorrenze dell'espressione precedente (trovare quanti più caratteri corrispondenti possibile). Per altre informazioni, vedere [Trova la corrispondenza una o più volte](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-).|+|`e.+d` trova "eed" in "feeder" ma non "ed".|
|Trovare la corrispondenza con qualsiasi carattere una o più volte (carattere jolly ?)|.+|`e.+e` trova "eede" in "feeder" ma non "ee".|
|Trovare la corrispondenza con zero o più occorrenze dell'espressione precedente (trovare quanti meno caratteri corrispondenti possibile). Per altre informazioni, vedere [Trova la corrispondenza zero o più volte (corrispondenza lazy)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-lazy-match-).|*?|`e.*?e` trova "ee" in "feeder" ma non "eede".|
|Trovare la corrispondenza con una o più occorrenze dell'espressione precedente (trovare quanti meno caratteri corrispondenti possibile). Per altre informazioni, vedere [Trova la corrispondenza una o più volte (corrispondenza lazy)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-lazy-match-).|+?|`e.+?e` trova "ente" e "erprise" in "enterprise", ma non l'intera parola "enterprise".|
|Ancorare la stringa di corrispondenza all'[inizio di una riga o stringa](/dotnet/standard/base-types/anchors-in-regular-expressions#start-of-string-or-line-)|^|`^car` trova la parola "car" solo quando viene visualizzata all'inizio di una riga.|
|Ancorare la stringa di corrispondenza alla [fine di una riga o stringa](/dotnet/standard/base-types/anchors-in-regular-expressions#end-of-string-or-line-)|\r?$|`end\r?$` trova "end" solo quando è visualizzato alla fine di una riga.|
|Ancorare la stringa di corrispondenza alla fine del file|$|`end$` trova "end" solo quando è visualizzato alla fine del file.|
|Trovare la corrispondenza con qualsiasi carattere singolo in un set|[abc]|`b[abc]` trova "ba", "bb" e "bc".|
|Trovare la corrispondenza con qualsiasi carattere in un intervallo di caratteri|[a-f]|`be[n-t]` trova "bet" in "between", "ben" in "beneath" e "bes" in "beside", ma non "below".|
|Acquisire e numerare in modo implicito l'espressione racchiusa tra parentesi|()|`([a-z])X\1` trova "aXa" e "bXb", ma non "aXb". "\1" fa riferimento al primo gruppo di espressioni "[a-z]". Per altre informazioni, vedere [Gruppi Capture e criteri di sostituzione](#capture-groups-and-replacement-patterns). |
|Invalidare una corrispondenza|(?!abc)|`real(?!ity)` trova "real" in "realty" e "really", ma non in "reality". Trova anche il secondo "real" (ma non il primo "real") in "realityreal".|
|Trovare la corrispondenza con qualsiasi carattere non presente in un determinato set di caratteri. Per altre informazioni, vedere [Gruppo di caratteri negativi](/dotnet/standard/base-types/character-classes-in-regular-expressions#negative-character-group-).|[^abc]|`be[^n-t]` trova "bef" in "before", "beh" in "behind" e "bel" in "below", ma non "beneath".|
|Trovare la corrispondenza con l'espressione prima o dopo il simbolo|&#124;|`(sponge|mud) bath` trova "sponge bath" e "mud bath".|
|[Far precedere dai caratteri di escape il carattere](/dotnet/standard/base-types/character-escapes-in-regular-expressions) che segue la barra rovesciata| \\ |`\^` trova il carattere ^.|
|Specificare il numero di occorrenze del gruppo o del carattere precedente. Per altre informazioni, vedere [Trova la corrispondenza esatta n volte](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-exactly-n-times-n).|{n}, dove 'n' è il numero di occorrenze|`x(ab){2}x` trova "xababx" e `x(ab){2,3}x` trova "xababx" e "xabababx" ma non "xababababx".|
|[Trovare la corrispondenza con un testo in una categoria Unicode](/dotnet/standard/base-types/character-classes-in-regular-expressions#unicode-category-or-unicode-block-p). Per altre informazioni sulle classi di caratteri Unicode, vedere [Proprietà dei caratteri Unicode standard 5.2](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf).|\p{X}, dove "X" è il numero Unicode.|`\p{Lu}` trova "T" e "D" in "Thomas Doe".|
|[Trovare la corrispondenza con un confine di parola](/dotnet/standard/base-types/anchors-in-regular-expressions#word-boundary-b)|\b (all'esterno di una classe di caratteri `\b` specifica un confine di parola e all'interno di una classe di caratteri `\b` specifica un backspace).|`\bin` trova "in" in "inside" ma non "pinto".|
|Trovare la corrispondenza con un'interruzione di riga (ovvero un ritorno a capo seguito da una nuova riga)|\r?\n|`End\r?\nBegin` trova "End" e "Begin" solo quando "End" è l'ultima stringa in una riga e "Begin" è la prima stringa nella riga successiva.|
|Trovare la corrispondenza con qualsiasi [carattere alfabetico](/dotnet/standard/base-types/character-classes-in-regular-expressions#word-character-w)|\w|`a\wd` trova "add" e "a1d", ma non "a d".|
|Trovare la corrispondenza con qualsiasi [carattere spazio vuoto](/dotnet/standard/base-types/character-classes-in-regular-expressions#whitespace-character-s)|\s|`Public\sInterface` trova la frase "Public Interface".|
|Trovare la corrispondenza con qualsiasi [carattere cifra decimale](/dotnet/standard/base-types/character-classes-in-regular-expressions#decimal-digit-character-d)|\d|`\d` trova "3" in "3456", "2" in 23" e "1" in "1".|
|Trovare la corrispondenza con un carattere Unicode|\uXXXX dove XXXX specifica il valore del carattere Unicode.|`\u0065` trova il carattere "e".|
|Trovare la corrispondenza con un identificatore|\b[\_\w-[0-9]][\_\w]*\b|Trova "type1" ma non "&type1" o "#define".|
|Trovare la corrispondenza con una stringa tra virgolette|((\\".+?\\")&#124;('.+?'))|Trova qualsiasi stringa racchiusa tra virgolette singole o doppie.|
|Trovare la corrispondenza con un numero esadecimale|\b0[xX]([0-9a-fA-F]+\)\b|Trova "0xc67f", ma non "0xc67g".|
|Trovare la corrispondenza con numeri interi e decimali|\b[0-9]*\\.\*[0-9]+\b|Trova "1.333".|

> [!TIP]
> Nei sistemi operativi Windows la maggior parte delle righe termina con "\r\n" (un ritorno a capo seguito da una nuova riga). Questi caratteri non sono visibili, ma sono presenti nell'editor e vengono passati al servizio delle espressioni regolari di .NET.

## <a name="capture-groups-and-replacement-patterns"></a>Gruppi Capture e criteri di sostituzione

Un gruppo Capture delinea una sottoespressione di un'espressione regolare e acquisisce una substring di una stringa di input. È possibile usare i gruppi Capture all'interno dell'espressione regolare stessa (ad esempio, per cercare una parola ripetuta) o in un criterio di sostituzione. Per informazioni dettagliate, vedere [Costrutti di raggruppamento nelle espressioni regolari](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions).

Per creare un gruppo Capture numerato, racchiudere la sottoespressione tra parentesi nel criterio dell'espressione regolare. Le acquisizioni sono numerate automaticamente da sinistra verso destra in base alla posizione delle parentesi di apertura nell'espressione regolare. Per accedere al gruppo Capture:

- **all'interno dell'espressione regolare**: Usare `\number`. Ad esempio, `\1` nell'espressione regolare `(\w+)\s\1` fa riferimento al primo gruppo Capture `(\w+)`.

- **in un criterio di sostituzione**: Usare `$number`. Ad esempio, l'espressione regolare raggruppata `(\d)([a-z])` definisce due gruppi: il primo gruppo contiene una singola cifra decimale e il secondo gruppo contiene un carattere singolo compreso tra **a** e **z**. L'espressione trova quattro corrispondenze nella stringa seguente: **1a 2b 3c 4d**. La stringa di sostituzione `z$1` fa riferimento solo al primo gruppo (`$1`) e converte la stringa in **z1 z2 z3 z4**.

L'immagine seguente mostra un'espressione regolare `(\w+)\s\1` e una stringa di sostituzione `$1`. Sia l'espressione regolare che il criterio di sostituzione fanno riferimento al primo gruppo Capture numerato automaticamente 1. Quando si sceglie **Sostituisci tutto** nella finestra di dialogo **Sostituzione veloce** in Visual Studio, le parole ripetute vengono rimosse dal testo.

![Sostituzione veloce che mostra un gruppo Capture numerato in Visual Studio](media/numbered-capture-group.png)

> [!TIP]
> Assicurarsi che il pulsante **Utilizza espressioni regolari** sia selezionato nella finestra di dialogo **Sostituzione veloce**.

### <a name="named-capture-groups"></a>Gruppi Capture denominati

Anziché usare la numerazione automatica di un gruppo Capture, è possibile assegnargli un nome. La sintassi per un gruppo Capture denominato è `(?<name>subexpression)`.

I gruppi Capture denominati, come i gruppi Capture numerati, possono essere usati all'interno dell'espressione regolare stessa o in un criterio di sostituzione. Per accedere al gruppo Capture denominato:

- **all'interno dell'espressione regolare**: Usare `\k<name>`. Ad esempio, `\k<repeated>` nell'espressione regolare `(?<repeated>\w+)\s\k<repeated>` fa riferimento al gruppo Capture denominato `repeated` la cui sottoespressione è `\w+`.

- **in un criterio di sostituzione**: Usare `${name}`. Ad esempio `${repeated}`.

A titolo di esempio, l'immagine seguente mostra un'espressione regolare `(?<repeated>\w+)\s\k<repeated>` e una stringa di sostituzione `${repeated}`. Sia l'espressione regolare che il criterio di sostituzione fanno riferimento al primo gruppo Capture denominato `repeated`. Quando si sceglie **Sostituisci tutto** nella finestra di dialogo **Sostituzione veloce** in Visual Studio, le parole ripetute vengono rimosse dal testo.

![Sostituzione veloce che mostra un gruppo Capture denominato in Visual Studio](media/named-capture-group.png)

> [!TIP]
> Assicurarsi che il pulsante **Utilizza espressioni regolari** sia selezionato nella finestra di dialogo **Sostituzione veloce**.

Per altre informazioni sui gruppi Capture denominati, vedere [Sottoespressioni corrispondenti denominate](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions#named-matched-subexpressions). Per altre informazioni sulle espressioni regolari usate nei criteri di sostituzione, vedere [Sostituzioni nelle espressioni regolari](/dotnet/standard/base-types/substitutions-in-regular-expressions).

## <a name="see-also"></a>Vedere anche

- [Linguaggio di espressioni regolari](/dotnet/standard/base-types/regular-expression-language-quick-reference)
- [Ricerca e sostituzione di testo](../ide/finding-and-replacing-text.md)
