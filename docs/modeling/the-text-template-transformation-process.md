---
title: Processo di trasformazione del modello di testo
description: Si apprenderà che il processo di trasformazione del modello di testo accetta un file modello di testo come input e genera un nuovo file di testo come output.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, transformation process
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8dc827039253c21effffcc82d70b4f66ff284738
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388594"
---
# <a name="the-text-template-transformation-process"></a>Processo di trasformazione del modello di testo
Il processo di trasformazione del modello di testo accetta un file modello di testo come input e genera un nuovo file di testo come output. Ad esempio, è possibile usare modelli di testo per generare Visual Basic codice C# o C# oppure è possibile generare un report HTML.

 A questo processo prendono parte tre componenti: il motore, l'host e i processori di direttiva. Il motore controlla il processo; interagisce con l'host e il processore di direttiva per produrre il file di output. L'host fornisce qualsiasi interazione con l'ambiente, ad esempio l'individuazione di file e assembly. Il processore di direttiva aggiunge funzionalità, ad esempio la lettura di dati da un file XML o da un database.

 Il processo di trasformazione del modello di testo viene eseguito in due passaggi. In primo luogo, il motore crea una classe temporanea, nota come classe di trasformazione generata. Questa classe contiene il codice generato dalle direttive e dai blocchi di controllo. Successivamente, il motore compila ed esegue la classe di trasformazione generata per produrre il file di output.

## <a name="components"></a>Componenti

|Componente|Descrizione|Personalizzabile (Sì/No)|
|-|-|-|
|Motore|Il componente motore controlla il processo di trasformazione del modello di testo|No.|
|Host|L'host è l'interfaccia tra il motore e l'ambiente utente. Visual Studio è un host del processo di trasformazione del testo.|Sì. È possibile scrivere un host personalizzato.|
|Processori di direttiva|I processori di direttiva sono classi che gestiscono le direttive nei modelli di testo. È possibile usare le direttive per fornire dati a un modello di testo da un'origine di input.|Sì. È possibile scrivere processori di direttive personalizzati|

## <a name="the-engine"></a>Il motore
 Il motore riceve il modello come stringa dall'host, che gestisce tutti i file usati nel processo di trasformazione. Il motore chiede quindi all'host di individuare eventuali processori di direttiva personalizzati e altri aspetti dell'ambiente. Il motore compila ed esegue quindi la classe di trasformazione generata. Il motore restituisce il testo generato all'host, che in genere salva il testo in un file.

## <a name="the-host"></a>L'host
 L'host è responsabile di qualsiasi elemento correlato all'ambiente esterno al processo di trasformazione, inclusi gli elementi seguenti:

- Individuazione di file di testo e binari richiesti dal motore o da un processore di direttiva. L'host può cercare le directory e la Global Assembly Cache per individuare gli assembly. L'host può individuare il codice del processore di direttiva personalizzato per il motore. L'host può anche individuare e leggere i file di testo e restituirne il contenuto come stringhe.

- Fornisce elenchi di assembly standard e spazi dei nomi usati dal motore per creare la classe di trasformazione generata.

- Specificare il dominio applicazione utilizzato quando il motore compila ed esegue la classe di trasformazione generata. Viene usato un dominio applicazione separato per proteggere l'applicazione host da errori nel codice del modello.

- Scrittura del file di output generato.

- Impostazione dell'estensione predefinita per il file di output generato.

- Gestione degli errori di trasformazione del modello di testo. Ad esempio, l'host può visualizzare gli errori nell'interfaccia utente o scriverli in un file. In Visual Studio, gli errori vengono visualizzati nella finestra del messaggio di errore.

- Fornire un valore di parametro obbligatorio se un utente ha chiamato una direttiva senza fornire un valore. Il processore di direttiva può specificare il nome della direttiva e il parametro e chiedere all'host di specificare un valore predefinito, se presente.

## <a name="directives-and-directive-processors"></a>Direttive e processori di direttive
 Una direttiva è un comando nel modello di testo. Fornisce parametri al processo di generazione. In genere le direttive definiscono l'origine e il tipo del modello o di altro input e l'estensione del file di output.

 Un processore di direttiva può elaborare una o più direttive. Quando si trasforma un modello, è necessario aver installato un processore di direttiva in grado di gestire le direttive nel modello.

 Le direttive funzionano aggiungendo codice nella classe di trasformazione generata. Le direttive vengono chiamate da un modello di testo e il motore elabora tutte le chiamate di direttiva quando crea la classe di trasformazione generata. Dopo aver chiamato correttamente una direttiva, il resto del codice scritto nel modello di testo può basarsi sulla funzionalità fornita dalla direttiva . Ad esempio, è possibile effettuare la chiamata seguente alla direttiva `import` nel modello:

 `<#@ import namespace="System.Text" #>`

 Il processore di direttiva standard lo converte in `using` un'istruzione nella classe transformation generata. È quindi possibile usare `StringBuilder` la classe nel resto del codice del modello senza qualificarla come `System.Text.StringBuilder` .
