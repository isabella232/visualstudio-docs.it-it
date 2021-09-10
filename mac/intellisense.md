---
title: IntelliSense
description: Informazioni sull'uso di IntelliSense in Visual Studio per Mac
author: cobey
ms.author: cobey
ms.date: 08/16/2019
ms.openlocfilehash: 07ef1d6292e4ac88ca616d0f35e3fd831cacc649
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964565"
---
# <a name="intellisense"></a>IntelliSense

IntelliSense offre varie funzionalità utili per migliorare l'esperienza di scrittura e modifica del codice. Oltre al completamento del codice, ad esempio, il motore di IntelliSense fornisce anche elenchi di membri, informazioni sui parametri e informazioni rapide.

In Visual Studio per Mac, IntelliSense viene fornito dal servizio dell'editor principale ed è supportato in molti linguaggi, ad esempio C#, XAML, F#, JavaScript e altri. Visual Studio per Mac include anche funzionalità IntelliSense avanzate, ad esempio la possibilità di visualizzare i completamenti da librerie non ancora importate nel progetto.

## <a name="code-completion"></a>Completamento del codice

Quando si digita in un file supportato, ad esempio un file di codice C#, i completamenti validi per la stringa digitata verranno visualizzati in un elenco di completamento e aggiornati durante la digitazione. Inoltre, se si elimina testo, l'elenco viene di nuovo aggiornato automaticamente per includere la più ampia gamma di possibilità per il completamento della stringa specificata. 

La finestra di completamento offre anche il supporto per filtrare i completamenti inclusi in base al tipo. Ad esempio, è possibile limitare i membri dell'elenco per rappresentare solo i tipi come classi o delegati. Questo processo di filtro può essere abilitato facendo clic su un'icona specifica che rappresenta il tipo che verrà filtrato o tramite scelte rapide da tastiera corrispondenti a un tipo specificato. Le icone, disponibili nella parte inferiore della finestra di completamento, sono le seguenti:

| Icona                         | NOME          | Parola chiave    | Tasto di scelta rapida |
| -----------------------------|---------------| -----------|--------|
| ![Icona di classe](media/classes-icon.png)  | classe         | `class`    |  ⌥C
| ![Icona Costante](media/constant-icon.png) | constant      | `const`    |  ⌥O
| ![Icona di delegato](media/delegate-icon.png) | delegato      | `delegate` |  ⌥D
| ![Icona di enumerazione](media/enums-icon.png)    | enum          | `enum`     |  ⌥E
| ![Icona di evento](media/event-icon.png)    | evento         |            |  ⌥V
| ![Icona Campo](media/fields-icon.png)   | campo         |            |  ⌥F
| ![Icona di interfaccia](media/interface-icon.png)| interfaccia     | `interface`|  ⌥I
| ![Icona di parola chiave](media/keyword-icon.png)  | parola chiave       |            |  ⌥K
| ![Icona di metodo](media/method-icon.png)   | method        |            |  ⌥M
| ![Icona di spazio dei nomi](media/namespace-icon.png)| namespace     | `namespace`|  ⌥N
| ![Icona di proprietà](media/props-icon.png)    | proprietà      |            |  ⌥P
| ![Icona di frammento di codice](media/snippet-icon.png)  | frammento di codice       | `class`    |  ⌥S
| ![Icona di struct](media/struct-icon.png)   | structure     | `struct`   |  ⌥S

Facendo clic su una delle icone o premendo i tasti di scelta rapida corrispondenti, l'elenco di completamento sarà limitato solo ai tipi definiti dal set di filtri.  

![Filtro di tipi IntelliSense](media/intellisense-typefiltering.gif)

## <a name="parameter-window"></a>Finestra dei parametri

Un'altra funzionalità di IntelliSense è la possibilità di fornire un elenco di parametri laddove appropriato. L'elenco di parametri fornisce informazioni dettagliate sulle firme dei metodi per il codice chiamato. Facendo clic sulle frecce verso l'alto o verso il basso all'interno della firma, è possibile scorrere tutte le firme dei parametri disponibili per determinare le più appropriate in base alle esigenze. Oltre ai dettagli dei tipi di dati consentiti, potrebbe essere disponibile anche una descrizione definita nel metodo di destinazione tramite commenti XML.

![Elenco parametri](media/intellisense-parameter.png)

Durante l'inserimento dei parametri, il parametro in corso di modifica sarà in grassetto, mentre i parametri inattivi avranno lo spessore standard. 


## <a name="triggering-completion-window-and-parameter-window"></a>Attivazione della finestra di completamento e della finestra dei parametri

La finestra di completamento verrà attivata automaticamente durante la digitazione nel file di origine. Tuttavia, è anche possibile attivare la finestra di completamento usando la combinazione di tasti `control-space`. Con questa combinazione di tasti l'elenco di completamento verrà visualizzato in corrispondenza della posizione corrente del punto di inserimento. 

È anche possibile attivare manualmente l'aspetto della finestra dei parametri digitando `control-shift-space`. Quando il punto di inserimento si trova nella posizione valida per un elenco di parametri, l'elenco di parametri verrà visualizzato vicino alla posizione del punto di inserimento.

## <a name="see-also"></a>Vedi anche

- [Azioni rapide (Visual Studio in Windows)](/visualstudio/ide/quick-actions)
- [Effettuare il refactoring del codice (Visual Studio in Windows)](/visualstudio/ide/refactoring-in-visual-studio)
