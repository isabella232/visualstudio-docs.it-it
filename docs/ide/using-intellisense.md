---
title: Informazioni sui parametri, elenco dei membri e informazioni rapide
description: 'Informazioni su come usare queste funzionalità di IntelliSense: Elenca membri, Informazioni sui parametri, Informazioni rapide e Completa parola.'
ms.custom: SEO-VS-2020
ms.date: 05/25/2018
ms.topic: conceptual
f1_keywords:
- vc.tools.intellisense
helpviewer_keywords:
- Quick info
- Parameter info
- Complete word
- List members
- IntelliSense [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 5d395a170a9daee3bfd4544b34fa1a203f6a9df9ba8d63d36266a7c588838548
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121399791"
---
# <a name="intellisense-in-visual-studio"></a>IntelliSense in Visual Studio

IntelliSense è lo strumenti di completamento del codice che include numerose funzionalità: Elenca membri, Informazioni sul parametro, Informazioni rapide e Completa parola. Queste funzionalità consentono di acquisire altre informazioni sul codice in uso, tengono traccia dei parametri che si digitano e aggiungono le chiamate a proprietà e metodi con poche sequenze di tasti.

Molti aspetti di IntelliSense sono specifici del linguaggio. Per altre informazioni su IntelliSense per linguaggi diversi, vedere gli argomenti elencati nella sezione [Vedere anche](#see-also).

## <a name="list-members"></a>Elenca membri

Un elenco di membri validi di un tipo (o dello spazio dei nomi) viene visualizzato dopo avere digitato un carattere del trigger, ad esempio un punto (`.`) nel codice gestito o `::` in C++. Se si continua a digitare caratteri, l'elenco viene filtrato per includere solo i membri o una *qualsiasi* parola all'interno del nome che iniziano con tali caratteri. IntelliSense esegue anche la corrispondenza con notazione Camel, pertanto è possibile digitare solo la prima lettera di ogni parola con notazione Camel nel nome del membro per visualizzare le corrispondenze.

Dopo aver selezionato un elemento, è possibile inserirlo nel codice premendo **TAB** o digitando uno spazio. Se si seleziona un elemento e si digita un punto, l'elemento viene visualizzato seguito dal punto; questa condizione comporta la visualizzazione di un altro elenco di membri. Quando si seleziona un elemento ma prima di inserirlo, vengono visualizzate informazioni rapide per l'elemento.

Nell'elenco dei membri, l'icona a sinistra rappresenta il tipo del membro, ad esempio spazio dei nomi, classe, funzione o variabile. Per un elenco di icone, vedere [Icone di Visualizzazione classi e Visualizzatore oggetti](../ide/class-view-and-object-browser-icons.md). L'elenco può essere piuttosto lungo, pertanto è possibile premere **PGSU** e **PGGIÙ** per spostarsi rispettivamente verso l'alto o verso il basso nell'elenco.

![Elenco dei membri di Visual Studio](../ide/media/vs2015_intellisense.png)

È possibile richiamare la funzionalità **Elenca membri** manualmente digitando **CTRL**+**J**, scegliendo **Modifica** > **IntelliSense** > **Elenca membri** o il pulsante **Elenca membri** sulla barra degli strumenti dell'editor. Se richiamato in una riga vuota o al di fuori di un ambito riconoscibile, l'elenco conterrà simboli dello spazio dei nomi globale.

Per disattivare Elenca membri per impostazione predefinita (in modo che non venga visualizzato a meno che non venga richiamato in modo specifico), passare a Opzioni strumenti Tutti i linguaggi e deselezionare Elenca automaticamente  >    >   **i membri**. Se si vuole disattivare la funzionalità Elenca membri solo per un linguaggio specifico, andare sulle impostazioni **Generali** per quel linguaggio.

È inoltre possibile modificare la modalità di suggerimento, in cui solo il testo digitato viene inserito nel codice. Ad esempio, se si immette un identificatore non presente nell'elenco e si preme **TAB,** in modalità di completamento la voce sostituirà l'identificatore tipiato. Per passare dalla modalità di completamento alla modalità suggerimento, premere **CTRL** ALT+BARRA SPAZIATRICE oppure scegliere Modifica Modalità di +  +    >  **completamento attiva/disattiva IntelliSense.**  >  

## <a name="parameter-info"></a>Informazioni sul parametro

Informazioni sul parametro fornisce informazioni relative al numero, ai nomi e ai tipi di parametri richiesti da un metodo, un parametro di tipo generico di attributo (in C#) o da un modello (in C++).

Il parametro in grassetto indica il parametro successivo richiesto durante la digitazione della funzione. Per le funzioni in overload, è possibile usare i tasti di direzione **Freccia SU** e **Freccia GIÙ** per visualizzare informazioni sui parametri alternativi per gli overload della funzione.

![Informazioni sul parametro](../ide/media/vs2015_param_info.png)

Se si annotano funzioni e parametri con commenti relativi alla documentazione XML, i commenti verranno visualizzati come informazioni sui parametri. Per altre informazioni, vedere [Inserire commenti XML per la generazione di documentazione](reference/generate-xml-documentation-comments.md).

È possibile richiamare manualmente Le informazioni sui parametri scegliendo Modifica informazioni parametri  >  **IntelliSense**, premendo  >    + **CTRL+MAIUSC+BARRA** +   SPAZIATRICE oppure scegliendo il pulsante Informazioni parametro sulla barra degli strumenti dell'editor.

## <a name="quick-info"></a>Informazioni rapide

Informazioni rapide visualizza la dichiarazione completa per ogni identificatore incluso nel codice.

![Informazioni rapide di Visual Studio](../ide/media/vs2015_quick_info.png)

Quando si seleziona un membro nella casella **Elenca membri**, vengono visualizzate anche le informazioni rapide.

![Informazioni sui parametri in un file di codice C&#35;](../ide/media/vs2015_paraminfo.png)

È possibile richiamare manualmente informazioni rapide scegliendo Modifica informazioni rapide  >  **IntelliSense**, premendo CTRL K, CTRL I o scegliendo il pulsante Informazioni rapide sulla barra degli  >    +   + strumenti dell'editor. 

Se una funzione è sottoposta a overload, è possibile che IntelliSense non visualizzi le informazioni per tutte le forme di overload.

È possibile disattivare le informazioni rapide per il codice C++ passando a Strumenti Opzioni Editor di testo  >    >    >  **C/C++** Avanzate e impostando Info rapide  >   **automaticamente** su `false` .

## <a name="complete-word"></a>Completa parola

Completa parola completa la digitazione del nome di una variabile, di un comando o di una funzione dopo che sono stati immessi caratteri sufficienti a identificare il termine in modo univoco. È possibile richiamare Completa parola scegliendo Modifica IntelliSense Completa parola , premendo CTRL+BARRA SPAZIATRICE oppure scegliendo il pulsante Completa parola sulla barra  >    >  degli  + strumenti dell'editor. 

## <a name="intellisense-options"></a>Opzioni IntelliSense

Le opzioni IntelliSense sono attive per impostazione predefinita. Per disattivarli, scegliere Strumenti Opzioni Editor di testo e deselezionare Informazioni sui parametri o Elenca membri automaticamente se non si vuole la  >    >   funzionalità Elenca membri.  

## <a name="intellisense-icons"></a>Icone di IntelliSense
Le icone in IntelliSense possono trasmettere un significato aggiuntivo con i modificatori di icona. Si tratta di stelle, cuori e lucchetti sovrapposti all'icona dell'oggetto per indicare, rispettivamente, che l'oggetto è protetto, interno o privato.

|    Icona    |    Accessibilità    |    Descrizione    |
|------------|--------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| ![Modificatore di icona per oggetto pubblico](../ide/media/intellisensePublicNoModifier.png)       |    Classe pubblica    |    L'accesso non è limitato.   |
| ![Modificatore di icona per oggetto protetto](../ide/media/intellisenseProtectedModifier.png)       |    Classe protetta    |    L'accesso è limitato alla classe o ai tipi derivati dalla classe che li contiene.    |
| ![Modificatore di icona per oggetto interno protetto](../ide/media/intellisenseProtectedInternalModifier.png)       |    Classe interna protetta    |    L'accesso è limitato all'assembly corrente o ai tipi derivati dalla classe che li contiene.    |
| ![Modificatore di icona per oggetto interno](../ide/media/intellisenseInternalModifier.png)       |    Classe interna    |    L'accesso è limitato all'assembly corrente.    |
|![Modificatore di icona per oggetto privato](../ide/media/intellisensePrivateModifier.png)        |    Classe privata    |    L'accesso è limitato alla classe o ai tipi derivati dalla classe che li contiene all'interno dell'assembly corrente. Disponibile da C# 7.2.    |

## <a name="troubleshoot-intellisense&quot;></a>Risolvere i problemi di IntelliSense

Le opzioni IntelliSense potrebbero non funzionare come previsto, in alcuni casi.

**Il cursore si trova sotto un errore del codice.** Non è possibile usare IntelliSense se una funzione incompleta o un altro errore esiste nel codice sopra il cursore perché IntelliSense potrebbe non essere in grado di analizzare gli elementi di codice. È possibile risolvere questo problema commentando il codice applicabile.

**Il cursore si trova in un commento del codice.** Non è possibile usare IntelliSense se il cursore si trova in un commento nel file di origine.

**Il cursore si trova in un valore letterale stringa.** Non è possibile usare IntelliSense se il cursore si trova tra virgolette intorno a un valore letterale stringa, come nel seguente esempio:

```cpp
MessageBox( hWnd, &quot;String literal|")
```

**Le opzioni automatiche sono disattivate.** Per impostazione predefinita, il funzionamento di IntelliSense è automatico, ma è possibile disabilitarlo. Anche se il completamento automatico delle istruzioni è disabilitato, è possibile richiamare una funzionalità IntelliSense.

## <a name="see-also"></a>Vedi anche

- [IntelliSense per Visual Basic](../ide/visual-basic-specific-intellisense.md)
- [IntelliSense per C#](../ide/visual-csharp-intellisense.md)
- [Python IntelliSense](../python/editing-python-code-in-visual-studio.md#intellisense)
- [IntelliSense per JavaScript](../ide/javascript-intellisense.md)
- [Codice di scrittura e refactoring (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [Inserire commenti XML per la generazione di documentazione](reference/generate-xml-documentation-comments.md)
