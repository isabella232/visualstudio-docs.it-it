---
title: Processo di trasformazione del modello di testo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, transformation process
ms.assetid: 80b3f0e0-49e7-4865-a1ac-dba068abe96b
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7322724b2118cb8b844262696a6e7cbd91a74e9b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658498"
---
# <a name="the-text-template-transformation-process"></a>Processo di trasformazione del modello di testo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il processo di trasformazione del modello di testo accetta un file modello di testo come input e genera un nuovo file di testo come output. È ad esempio possibile utilizzare modelli di testo per generare Visual Basic o C# codice oppure generare un report HTML.

 Tre componenti fanno parte di questo processo: il motore, l'host e i processori di direttiva. Il motore controlla il processo; interagisce con l'host e il processore di direttiva per produrre il file di output. L'host fornisce qualsiasi interazione con l'ambiente, ad esempio l'individuazione di file e assembly. Il processore di direttiva aggiunge funzionalità, ad esempio la lettura di dati da un file XML o da un database.

 Il processo di trasformazione del modello di testo viene eseguito in due passaggi. In primo luogo, il motore crea una classe temporanea, nota come classe Transformation generata. Questa classe contiene il codice generato dalle direttive e dai blocchi di controllo. Successivamente, il motore compila ed esegue la classe Transformation generata per produrre il file di output.

## <a name="components"></a>Componenti

|Componente|Descrizione|Personalizzabile (sì/no)|
|---------------|-----------------|------------------------------|
|Motore|Il componente motore controlla il processo di trasformazione del modello di testo|No.|
|Host|L'host è l'interfaccia tra il motore e l'ambiente utente. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] è un host del processo di trasformazione del testo.|Sì. È possibile scrivere un host personalizzato.|
|Processori di direttiva|I processori di direttiva sono classi che gestiscono le direttive nei modelli di testo. È possibile utilizzare le direttive per fornire dati a un modello di testo da un'origine di input.|Sì. È possibile scrivere processori di direttiva personalizzati|

## <a name="the-engine"></a>Motore
 Il motore riceve il modello come stringa dall'host, che gestisce tutti i file utilizzati nel processo di trasformazione. Il motore chiede quindi all'host di individuare tutti i processori di direttiva personalizzati e altri aspetti dell'ambiente. Il motore compila quindi ed esegue la classe Transformation generata. Il motore restituisce il testo generato all'host, che in genere Salva il testo in un file.

## <a name="the-host"></a>L'host
 L'host è responsabile di tutto ciò che si riferisce all'ambiente al di fuori del processo di trasformazione, incluse le seguenti:

- Individuazione dei file di testo e binari richiesti dal motore o da un processore di direttiva. L'host può cercare le directory e il Global Assembly Cache per individuare gli assembly. L'host può individuare il codice del processore di direttiva personalizzato per il motore. L'host può anche individuare e leggere i file di testo e restituire il relativo contenuto come stringhe.

- Fornire elenchi di assembly e spazi dei nomi standard usati dal motore per creare la classe Transformation generata.

- Specificando il dominio applicazione utilizzato quando il motore compila ed esegue la classe Transformation generata. Viene utilizzato un dominio applicazione separato per proteggere l'applicazione host dagli errori nel codice del modello.

- Scrittura del file di output generato.

- Impostazione dell'estensione predefinita per il file di output generato.

- Gestione degli errori di trasformazione del modello di testo. Ad esempio, l'host può visualizzare gli errori nell'interfaccia utente o scriverli in un file. In [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] gli errori vengono visualizzati nella finestra del messaggio di errore.

- Fornire un valore di parametro obbligatorio se un utente ha chiamato una direttiva senza fornire un valore. Il processore di direttiva può specificare il nome della direttiva e il parametro e richiedere all'host di fornire un valore predefinito, se disponibile.

## <a name="directives-and-directive-processors"></a>Direttive e processori di direttiva
 Una direttiva è un comando nel modello di testo. Fornisce parametri per il processo di generazione. In genere le direttive definiscono l'origine e il tipo del modello o di altri input e l'estensione del nome file del file di output.

 Un processore di direttiva può elaborare una o più direttive. Quando si trasforma un modello, è necessario avere installato un processore di direttiva che possa gestire le direttive nel modello.

 Le direttive funzionano aggiungendo codice nella classe Transformation generata. È possibile chiamare le direttive da un modello di testo e il motore elabora tutte le chiamate di direttiva quando crea la classe Transformation generata. Dopo aver chiamato correttamente una direttiva, il resto del codice scritto nel modello di testo può basarsi sulla funzionalità fornita dalla direttiva. Ad esempio, è possibile effettuare la chiamata seguente alla direttiva `import` nel modello:

 `<#@ import namespace="System.Text" #>`

 Il processore di direttiva standard converte questo oggetto in un'istruzione `using` nella classe Transformation generata. È quindi possibile usare la classe `StringBuilder` nel resto del codice del modello senza qualificarla come `System.Text.StringBuilder`.
