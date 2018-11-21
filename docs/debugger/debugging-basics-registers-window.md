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
ms.openlocfilehash: 0219418b754c93b8e5e50997ede73e0611ed496a
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257056"
---
# <a name="about-the-registers-window-in-visual-studio-c-c-visual-basic-f"></a>Informazioni sulla finestra Registri in Visual Studio (C#, C++, Visual Basic, F#)

Il **registra** è disponibile solo se è abilitato il debug a livello di indirizzo nella finestra di **opzioni** della finestra di dialogo **debug** nodo.  
  
 I registri sono speciali posizioni interne a un processore (CPU) utilizzate per archiviare piccole porzioni di dati attualmente in uso da parte del processore. Durante la compilazione o l'interpretazione di codice sorgente vengono generate istruzioni che spostano dati dalla memoria ai registri e viceversa, secondo necessità. Poiché l'accesso ai dati contenuti nei registri è molto rapido se confrontato all'accesso ai dati in memoria, il codice che consente al processore la conservazione dei dati in un registro e l'accesso ripetuto ad essi tende a essere eseguito più velocemente rispetto al codice che impone al processore di caricare e scaricare continuamente i registri.	 Per facilitare la conservazione dei dati nei registri da parte del compilatore ed eseguire ulteriori ottimizzazioni è consigliabile evitare l'utilizzo di variabili globali e basarsi il più possibile su variabili locali. Il codice scritto in questo modo viene definito come dotato di un buon posizionamento dei riferimenti. In alcuni linguaggi, quali C/C++, il programmatore può dichiarare una variabile di registro, imponendo così al compilatore di conservare sempre, per quanto possibile, la variabile in un registro. Per altre informazioni, vedere [parola chiave Register](https://msdn.microsoft.com/library/5b66905a-2f7f-4918-bb55-5e66d4bc50f9).  
  
 I registri possono essere distinti in due tipi: registri di utilizzo generale e registri di utilizzo specifico. Nei registri di utilizzo generale sono contenuti dati relativi a operazioni generali quali la somma di due numeri o l'aggiunta del riferimento a un elemento in una matrice. I registri di utilizzo specifico hanno scopi e significato particolari. Un esempio illuminante è il registro dei puntatori dello stack, utilizzato dal processore per tenere traccia dello stack di chiamate del programma. Con molta probabilità, il programmatore non intenderà modificare direttamente il puntatore dello stack. La sua presenza, tuttavia, è essenziale per il corretto funzionamento del programma. Senza il puntatore dello stack, infatti, non vi sarebbero informazioni chiare su quale punto del programma deve essere raggiunto al termine di una chiamata di funzione.  
  
 Nella maggior parte dei registri di utilizzo generale è contenuto un singolo elemento di dati, ad esempio un singolo integer, un singolo numero a virgola mobile o un singolo elemento di una matrice. Alcuni processori più recenti dispongono di registri più capaci, denominati registri vettoriali, che possono contenere una piccola matrice di dati. Poiché possono contenere un numero così elevato di dati, con i registri vettoriali è possibile eseguire operazioni che implicano l'esecuzione molto rapida di matrici. I registri vettoriali, utilizzati da principio su costosi computer molto potenti e ad elevate prestazioni, cominciano a essere disponibili sui microprocessori, in cui vengono impiegati per gli enormi vantaggi offerti nelle attività grafiche a utilizzo intensivo di risorse.  
  
 In un processore sono, in genere, disponibili due insiemi di registri di utilizzo generale, uno ottimizzato per le operazioni con virgola mobile e l'altro per le operazioni su numeri interi. Per questo sono denominati, rispettivamente, registri a virgola mobile e registri interi.  
  
 Il codice gestito viene compilato in fase di esecuzione in codice nativo che accede ai registri fisici del microprocessore. Il **registra** finestra Visualizza i registri fisici per common language runtime o codice nativo. Il **registra** finestra non visualizza informazioni di registro per applicazioni script o SQL, perché lo script e SQL sono lingue che non supportano il concetto di registro.  
  
 Per altre informazioni sulla visualizzazione di **registra** finestra, vedere [usando la finestra Registri](../debugger/how-to-use-the-registers-window.md).  
  
 Quando si esamina il **registra** finestra, si noteranno voci, ad esempio `EAX = 003110D8`.  
  
 Il simbolo a sinistra del `=` segno è il nome del registro `EAX`, in questo caso. Il numero a destra del `=` sign rappresenta il contenuto del registro.  
  
 Il **registra** finestra consente di eseguire più della semplice visualizzazione di contenuto di un registro. Se si sta utilizzando codice nativo in modalità di interruzione, è possibile fare clic sul contenuto di un registro e modificarne il valore. Si tratta di un'operazione che deve essere eseguita con criterio. Se non si comprende la funzione del registro che si sta modificando e quali dati esso contenga, un'incauta modifica provocherà, con molta probabilità, un arresto anomalo del programma o altri effetti indesiderati. Una spiegazione dettagliata degli insiemi di registri dei vari processori Intel e compatibili, tuttavia, eccede l'ambito di questa breve introduzione.  
  
## <a name="register-groups"></a>Gruppi di registri  
 Per evitare confusione, il **registra** finestra i registri sono organizzati in gruppi. Se facendo clic sui **registra** finestra, verrà visualizzato un menu di scelta rapida contenente un elenco di gruppi, che è possibile visualizzare o nascondere secondo necessità.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: usare la finestra registri](../debugger/how-to-use-the-registers-window.md)   
 [Debugger Basics](../debugger/getting-started-with-the-debugger.md) (Nozioni di base sul debugger)