---
title: Informazioni sulla finestra registri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, about Registers window
- debugging [Visual Studio], Registers window
ms.assetid: ab354047-053e-4f94-8ac1-26e761442b6f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5364bf8ba45e4b569649920175c6e94fc46128ed
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/18/2018
ms.locfileid: "53561801"
---
# <a name="about-the-registers-window-in-visual-studio-c-c-visual-basic-f"></a>Informazioni sulla finestra Registri in Visual Studio (C#, C++, Visual Basic, F#)

La finestra **Registri** è disponibile solo se il debug a livello di indirizzo è stato attivato nella finestra di dialogo **Opzioni**, nodo **Debug**.  
  
 I registri sono speciali posizioni interne a un processore (CPU) utilizzate per archiviare piccole porzioni di dati attualmente in uso da parte del processore. Durante la compilazione o l'interpretazione di codice sorgente vengono generate istruzioni che spostano dati dalla memoria ai registri e viceversa, secondo necessità. L'accesso ai dati nei registri è molto veloce rispetto all'accesso ai dati in memoria, il codice che consente al processore di mantenere i dati in un registro di sistema e accedervi ripetutamente tende a essere eseguito più velocemente rispetto al codice che richiede il processore per caricare e scaricare i registri continuamente. Per facilitare la conservazione dei dati nei registri da parte del compilatore ed eseguire ulteriori ottimizzazioni è consigliabile evitare l'utilizzo di variabili globali e basarsi il più possibile su variabili locali. Il codice scritto in questo modo viene definito come dotato di un buon posizionamento dei riferimenti. In alcuni linguaggi, quali C/C++, il programmatore può dichiarare una variabile di registro, imponendo così al compilatore di conservare sempre, per quanto possibile, la variabile in un registro. Per altre informazioni, vedere [Parola chiave register](https://msdn.microsoft.com/library/5b66905a-2f7f-4918-bb55-5e66d4bc50f9).  
  
 I registri possono essere distinti in due tipi: registri di utilizzo generale e registri di utilizzo specifico. Nei registri di utilizzo generale sono contenuti dati relativi a operazioni generali quali la somma di due numeri o l'aggiunta del riferimento a un elemento in una matrice. I registri di utilizzo specifico hanno scopi e significato particolari. Un esempio illuminante è il registro dei puntatori dello stack, utilizzato dal processore per tenere traccia dello stack di chiamate del programma. Con molta probabilità, il programmatore non intenderà modificare direttamente il puntatore dello stack. La sua presenza, tuttavia, è essenziale per il corretto funzionamento del programma. Senza il puntatore dello stack, infatti, non vi sarebbero informazioni chiare su quale punto del programma deve essere raggiunto al termine di una chiamata di funzione.  
  
 Nella maggior parte dei registri di utilizzo generale è contenuto un singolo elemento di dati, ad esempio un singolo integer, un singolo numero a virgola mobile o un singolo elemento di una matrice. Alcuni processori più recenti dispongono di registri più capaci, denominati registri vettoriali, che possono contenere una piccola matrice di dati. Poiché possono contenere un numero così elevato di dati, con i registri vettoriali è possibile eseguire operazioni che implicano l'esecuzione molto rapida di matrici. I registri vettoriali, utilizzati da principio su costosi computer molto potenti e ad elevate prestazioni, cominciano a essere disponibili sui microprocessori, in cui vengono impiegati per gli enormi vantaggi offerti nelle attività grafiche a utilizzo intensivo di risorse.  
  
 In un processore sono, in genere, disponibili due insiemi di registri di utilizzo generale, uno ottimizzato per le operazioni con virgola mobile e l'altro per le operazioni su numeri interi. Per questo sono denominati, rispettivamente, registri a virgola mobile e registri interi.  
  
 Il codice gestito viene compilato in fase di esecuzione in codice nativo che accede ai registri fisici del microprocessore. I registri fisici per codice eseguito in Common Language Runtime e codice nativo sono visualizzati nella finestra **Registri**. Nella finestra **Registri** non vengono visualizzate informazioni di registro per applicazioni script o SQL, dal momento che i linguaggi script ed SQL non supportano il concetto di registro.  
  
 Per altre informazioni sulla visualizzazione della finestra **Registri**, vedere [Uso della finestra Registri](../debugger/how-to-use-the-registers-window.md).  
  
 Quando si esamina il **registra** finestra, si noteranno voci, ad esempio `EAX = 003110D8`.  
  
 Il simbolo a sinistra del `=` segno è il nome del registro `EAX`, in questo caso. Il numero alla destra del segno `=` rappresenta il contenuto del registro.  
  
 Oltre a esaminare il contenuto di un registro, nella finestra **Registri** è possibile eseguire altre attività. Se si sta utilizzando codice nativo in modalità di interruzione, è possibile fare clic sul contenuto di un registro e modificarne il valore. Si tratta di un'operazione che deve essere eseguita con criterio. Se non si comprende la funzione del registro che si sta modificando e quali dati esso contenga, un'incauta modifica provocherà, con molta probabilità, un arresto anomalo del programma o altri effetti indesiderati. Una spiegazione dettagliata degli insiemi di registri dei vari processori Intel e compatibili, tuttavia, eccede l'ambito di questa breve introduzione.  
  
## <a name="register-groups"></a>Gruppi di registri  
 Per evitare confusione, nella finestra **Registri** i registri sono organizzati in gruppi. Facendo clic con il pulsante destro del mouse sulla finestra **Registri** verrà visualizzato un menu di scelta rapida in cui sono elencati i gruppi, che è possibile visualizzare o nascondere secondo necessità.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Utilizzare la finestra registri](../debugger/how-to-use-the-registers-window.md)   
 [Presentazione del debugger](../debugger/debugger-feature-tour.md)