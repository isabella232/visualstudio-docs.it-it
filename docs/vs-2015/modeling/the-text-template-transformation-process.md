---
title: Il processo di trasformazione del modello testo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, transformation process
ms.assetid: 80b3f0e0-49e7-4865-a1ac-dba068abe96b
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0f92b4053006aa5da3c28d9330b372466f84d0fd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199965"
---
# <a name="the-text-template-transformation-process"></a>Processo di trasformazione del modello di testo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il processo di trasformazione del modello testo accetta un file di modello di testo come input e genera un nuovo file di testo come output. Ad esempio, è possibile usare i modelli di testo per generare codice Visual Basic o c# oppure è possibile generare un report HTML.  
  
 Tre componenti di partecipano a questo processo: il motore, l'host e i processori di direttiva. Il motore controlla il processo. interagisce con l'host e il processore di direttiva per generare il file di output. L'host fornisce qualsiasi interazione con l'ambiente, ad esempio l'individuazione di assembly e file. Il processore di direttiva aggiunge funzionalità, ad esempio la lettura dei dati da un file XML o un database.  
  
 Il processo di trasformazione del modello testo viene eseguito in due passaggi. In primo luogo, il motore crea una classe temporanea, che è noto come la classe transformation generata. Questa classe contiene il codice generato dalle direttive e i blocchi di controllo. Successivamente, il motore compila ed esegue la classe transformation generata per produrre il file di output.  
  
## <a name="components"></a>Componenti  
  
|Componente|Descrizione|Personalizzabile (Sì/No)|  
|---------------|-----------------|------------------------------|  
|Engine (Motore)|Il componente del motore consente di controllare il processo di trasformazione del modello testo|No.|  
|Host|L'host è l'interfaccia tra il motore e l'ambiente utente. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] è un host del processo di trasformazione del testo.|Sì. È possibile scrivere un host personalizzato.|  
|Processori di direttiva|Processori di direttiva sono classi che gestiscono le direttive nei modelli di testo. È possibile utilizzare le direttive per fornire dati a un modello di testo da un'origine di input.|Sì. È possibile scrivere processori di direttiva personalizzati|  
  
## <a name="the-engine"></a>Il motore di  
 Il motore riceve il modello sotto forma di stringa dall'host, che gestisce tutti i file che vengono usati nel processo di trasformazione. Il motore richiede quindi l'host per individuare tutti i processori di direttiva personalizzati e altri aspetti dell'ambiente. Quindi, il motore viene compilata e viene eseguita la classe transformation generata. Il motore restituisce il testo generato per l'host, che normalmente consente di salvare il testo in un file.  
  
## <a name="the-host"></a>L'host  
 L'host è responsabile per qualsiasi elemento che si riferisce all'ambiente all'esterno del processo di trasformazione, incluse le seguenti:  
  
- Individuazione file di testo e binari richiesti dal motore o un processore di direttiva. L'host può cercare le directory e global assembly cache per individuare gli assembly. L'host può individuare il codice di processore di direttiva personalizzato per il motore. L'host può anche individuare e leggere i file di testo e restituire il rispettivo contenuto sotto forma di stringhe.  
  
- Fornendo elenchi di assembly standard e gli spazi dei nomi che vengono utilizzati dal motore per creare la classe transformation generata.  
  
- Fornire il dominio dell'applicazione che viene usato quando il motore compila ed esegue la classe transformation generata. Un dominio di applicazione separata viene utilizzato per proteggere l'applicazione host dagli errori nel codice del modello.  
  
- La scrittura del file di output generato.  
  
- Impostazione dell'estensione predefinita per il file di output generato.  
  
- La gestione degli errori di trasformazione del modello testo. Ad esempio, l'host può visualizzare gli errori nell'interfaccia utente o scriverli in un file. (In [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], gli errori vengono visualizzati nella finestra di messaggio di errore.)  
  
- Se un utente ha definito una direttiva senza fornire un valore, che fornisce un valore di parametro obbligatorio. Il processore di direttiva è possibile specificare il nome della direttiva e il parametro e chiedere all'host di fornire un valore predefinito se presente.  
  
## <a name="directives-and-directive-processors"></a>Direttive e i processori di direttiva  
 Una direttiva è un comando nel modello di testo. Fornisce i parametri per il processo di generazione. In genere, le direttive definiscono l'origine e il tipo di modello o altri tipi di input e l'estensione del file di output.  
  
 Un processore di direttiva può elaborare uno o più direttive. Quando si trasforma un modello, è necessario aver installato un processore di direttiva che può gestire le direttive nel modello.  
  
 Direttive funzionano mediante l'aggiunta di codice nella classe transformation generata. È consigliabile chiamare direttive da un modello di testo e il motore elabora tutte le chiamate direttive durante la creazione della classe transformation generata. Dopo aver chiamato una direttiva correttamente, il resto del codice scritto nel modello di testo può basarsi sulle funzionalità che fornisce la direttiva. Ad esempio, si può effettuare la chiamata seguente per il `import` direttiva del modello:  
  
 `<#@ import namespace="System.Text" #>`  
  
 Il processore di direttiva standard converte questo a un `using` istruzione nella classe transformation generata. È quindi possibile usare la `StringBuilder` nella parte restante del codice del modello senza qualificare con il nome classe `System.Text.StringBuilder`.
