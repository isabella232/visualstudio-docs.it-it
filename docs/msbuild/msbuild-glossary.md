---
title: Glossario di MSBuild
description: Informazioni sui Microsoft Build Engine (MSBuild) che descrivono il motore di compilazione e i relativi componenti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f767d8e4-24d8-4803-80eb-e857202dbe2c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 3da3236b9d8cef954c4457b5710956751679b059
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122085026"
---
# <a name="msbuild-glossary"></a>Glossario di MSBuild

Questi termini vengono usati per descrivere Microsoft Build Engine (MSBuild) e i relativi componenti.

## <a name="assemblyfoldersex"></a>AssemblyFoldersEx

Percorso del Registro di sistema in cui i fornitori di terze parti archiviano i percorsi per ogni versione del framework supportato, che la risoluzione in fase di progettazione può esaminare per trovare gli assembly di riferimento.

## <a name="batching"></a>divisione in batch

La divisione in batch consiste nel dividere gli elementi in categorie diverse note come *batch*, in base ai metadati degli elementi, e quindi nell'eseguire una destinazione o un'attività una sola volta usando ogni batch. La divisione in batch è l'equivalente MSBuild del costrutto for--loop. Per altre informazioni, vedere [Batch](../msbuild/msbuild-batching.md).

## <a name="build-scope"></a>ambito di compilazione

L' ambito di compilazione descrive un oggetto MSBuild, ad esempio una proprietà globale, potenzialmente visibile a un progetto e ai progetti figlio creati in una compilazione a più progetti.

## <a name="child-project"></a>progetto figlio

Vedere *progetto, figlio*.

## <a name="condition"></a>condizione

Diversi elementi di MSBuild possono essere definiti in modo condizionale, vale a dire che l'attributo `Condition` viene visualizzato nell'elemento. Il contenuto degli elementi condizionali viene elaborato solo se la condizione risulta essere `true`. Per altre informazioni, vedere [Condizioni](../msbuild/msbuild-conditions.md).

## <a name="definition-item"></a>definizione, elemento

Vedere *definizione di un elemento*.

## <a name="emit-item"></a>creazione di un elemento

Durante la fase di esecuzione di una compilazione, gli elementi possono essere creati o modificati dalle attività che hanno elementi `Output` figlio che hanno l'attributo `ItemName`. Si dice che l'attività "crea" i nuovi elementi.

## <a name="emit-property"></a>creare una proprietà

Durante la fase di esecuzione di una compilazione, le proprietà possono essere create o modificate dalle attività che hanno elementi `Output` figlio che hanno l'attributo `PropertyName`. Si dice che l'attività "crea" la nuova proprietà.

## <a name="evaluation-phase"></a>fase di valutazione

La valutazione è la prima fase della compilazione di un progetto. Tutte le proprietà e gli elementi vengono valutati nell'ordine in cui sono visualizzati nel progetto. I progetti importati vengono valutati quando vengono rilevati nel progetto. Le destinazioni e le attività non vengono eseguite fino alla fase di esecuzione ed eventuali proprietà o elementi dichiarati o creati vengono ignorati durante la valutazione.

## <a name="execution-phase"></a>fase di esecuzione

L'esecuzione è la seconda fase della compilazione di un progetto. Le destinazioni selezionate vengono compilate e le attività vengono eseguite. Le proprietà e gli elementi possono essere creati o modificati rispetto ai valori di valutazione.

## <a name="function-property"></a>funzione, proprietà

Vedere *funzione di proprietà*.

## <a name="function-item"></a>funzione, Item

Vedere funzione Item.

## <a name="item"></a>item

Gli elementi sono input nel sistema di compilazione e vengono raggruppati in tipi di elemento in base ai nomi degli elementi. Gli elementi rappresentano in genere file. Poiché gli elementi vengono denominati in base al tipo di elemento a cui appartengono, i termini *elemento* e *valore dell'elemento* sono interscambiabili. Per altre informazioni, vedere [Elementi](../msbuild/msbuild-items.md).

## <a name="item-definition"></a>definizione di un elemento

I gruppi di definizioni di elementi contengono definizioni di elementi che aggiungono metadati predefiniti a qualsiasi tipo di elemento. Come i metadati noti, i metadati predefiniti sono associati a tutti gli elementi del tipo di elemento specificato. È possibile eseguire l'override esplicito dei metadati predefiniti nella definizione di un elemento. Per altre informazioni, vedere [Definizioni di elementi](../msbuild/item-definitions.md).

## <a name="item-function"></a>funzione Item

Le funzioni Item ottengono informazioni sugli elementi nel progetto. Queste funzioni semplificano l'acquisizione di elementi Distinct() e sono più veloci rispetto allo scorrimento in ciclo degli elementi. Queste funzioni servono a modificare le stringhe e i percorsi degli elementi. Per altre informazioni, vedere [Funzioni degli elementi](../msbuild/item-functions.md).

## <a name="item-metadata"></a>metadati degli elementi

Vedere *metadati, elemento*.

## <a name="item-type"></a>tipo di elemento

I tipi di elementi sono elenchi denominati di elementi che possono essere usati come parametri per le attività. Le attività usano i valori degli elementi per eseguire i passaggi del processo di compilazione. Per altre informazioni, vedere [Elementi](../msbuild/msbuild-items.md).

## <a name="metadata-item"></a>metadati, elemento

I metadati di un elemento sono una raccolta di coppie nome-valore associate a un elemento. I metadati forniscono informazioni descrittive per l'elemento e sono facoltativi, eccetto i metadati noti. Per altre informazioni, vedere [Elementi](../msbuild/msbuild-items.md).

## <a name="metadata-well-known"></a>metadati, noti

I metadati noti sono i metadati degli elementi di sola lettura che vengono inizializzati usando un valore predefinito. I metadati noti forniscono informazioni descrittive per un elemento che fa riferimento a un file. Ad esempio, il valore dei metadati noti denominati `FullPath` è il percorso completo del file di riferimento. Per altre informazioni, vedere [Elementi](../msbuild/msbuild-items.md).

## <a name="multitargeting"></a>multitargeting

Possibilità per un progetto di applicazione o assembly di specificare come destinazione più CLR e framework diversi da MSBuild e da Visual Studio.

## <a name="profile"></a>profile

Subset del framework completo. Viene usato per ridurre al minimo la quantità di dati che è necessario scaricare in un computer.

## <a name="project-file"></a>file di progetto

Un file di progetto contiene lo script di MSBuild che controlla la compilazione. I file di progetto hanno generalmente un'estensione che termina con *proj*, ad esempio *csproj* o *vbproj*. I file di progetto possono importare file di proprietà e file di destinazione.

## <a name="property"></a>proprietà

Una proprietà è una coppia chiave-valore usata per controllare il processo di compilazione. Per altre informazioni, vedere MSBuild [proprietà .](../msbuild/msbuild-properties.md)

## <a name="property-environment"></a>proprietà, ambiente

Una proprietà dell'ambiente è una proprietà che viene automaticamente inizializzata sul valore di una variabile di ambiente di sistema con lo stesso nome. Per altre informazioni, vedere MSBuild [proprietà .](../msbuild/msbuild-properties.md)

## <a name="property-file"></a>file di proprietà

Un file di proprietà è un file di progetto che contiene principalmente gruppi di proprietà e gruppi di elementi che forniscono indicazioni per la compilazione. Per convenzione, l'estensione di file è *props*. I file di proprietà vengono in genere importati all'inizio dei file di progetto associati.

## <a name="property-function"></a>proprietà, funzione

Una funzione di proprietà è una proprietà di sistema o un metodo che si può usare per valutare gli script di MSBuild. I metodi di proprietà possono essere usati per leggere l'ora di sistema, confrontare stringhe, trovare la corrispondenza per espressioni regolari ed eseguire altre azioni. Per altre informazioni, vedere [Funzioni delle proprietà](../msbuild/property-functions.md).

## <a name="property-function-nested"></a>funzione di proprietà, annidata

Le funzioni di proprietà possono essere combinate per formare funzioni più complesse. Ad esempio,

 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`

Per altre informazioni, vedere [Funzioni delle proprietà](../msbuild/property-functions.md).

## <a name="property-global"></a>proprietà, globale

Una proprietà globale è una coppia chiave-valore usata per controllare il processo di compilazione. Le proprietà globali vengono impostate al prompt dei comandi oppure usando l'attributo `Properties` di un'[attività di MSBuild](../msbuild/msbuild-task.md) e non possono essere modificate durante la fase di valutazione di una compilazione. Per altre informazioni, vedere MSBuild [proprietà .](../msbuild/msbuild-properties.md)

## <a name="property-local"></a>proprietà, locale

Una proprietà locale è una coppia chiave-valore usata per controllare il processo di compilazione. Questo termine viene usato solo per distinguere una proprietà che non è una proprietà globale.

## <a name="property-registry"></a>proprietà, Registro di sistema

Una proprietà del Registro di sistema ha un valore che viene impostato usando una speciale sintassi che legge il valore di una sottochiave del Registro di sistema. Per altre informazioni, vedere MSBuild [proprietà .](../msbuild/msbuild-properties.md)

## <a name="property-reserved"></a>proprietà, riservata

Una proprietà riservata è una coppia chiave-valore usata per controllare il processo di compilazione. Le proprietà riservate vengono automaticamente inizializzate su valori predefiniti. Per altre informazioni, vedere MSBuild [proprietà .](../msbuild/msbuild-properties.md)

## <a name="project-scope"></a>ambito di progetto

L'ambito del progetto descrive un oggetto di MSBuild, ad esempio una proprietà locale, visibile solo nel file di progetto contenitore e ai progetti importati.

## <a name="project-child"></a>progetto, figlio

Un progetto figlio viene creato dall'attività di MSBuild durante la compilazione di un progetto. Questo nuovo progetto è figlio del progetto che contiene o importa la destinazione contenente l'attività di MSBuild. Il progetto figlio eredita le proprietà globali del progetto padre, a meno che non vengano modificate dall'attributo `Properties`.

## <a name="redist-list"></a>elenco redist

Elenco di ridistribuzione: elenco di assembly corrispondenti a un determinato framework.

## <a name="reference-assembly"></a>assembly di riferimento

Assembly usato in fase di progettazione per creare un'applicazione. È possibile rimuovere da un assembly di riferimento il codice effettivo e le interfacce private, lasciando solo i metadati e le interfacce pubbliche.

## <a name="registry-property"></a>proprietà del Registro di sistema

Vedere *proprietà, Registro di sistema*.

## <a name="target"></a>target

Una destinazione raggruppa le attività in un determinato ordine ed espone le sezioni del file di progetto come punti di ingresso al processo di compilazione. Per altre informazioni, vedere [Destinazioni](../msbuild/msbuild-targets.md).

## <a name="target-building"></a>destinazione, compilazione

Vedere destinazione, esecuzione.

## <a name="target-evaluating"></a>destinazione, valutazione

A causa della compilazione incrementale, le destinazioni devono essere analizzate per trovare le potenziali modifiche alle proprietà e agli elementi. Anche se la destinazione viene ignorata, è necessario effettuare queste modifiche. Valutare una destinazione significa eseguire questa analisi e apportare tali modifiche. Per altre informazioni, vedere [Compilazioni incrementali](../msbuild/incremental-builds.md).

## <a name="target-executing"></a>destinazione, esecuzione

Eseguire una destinazione significa valutarla ed eseguire tutte le attività che non hanno condizioni o le cui condizioni restituiscono true. Durante la compilazione incrementale, le destinazioni possono essere ignorate o eseguite, ma vengono sempre valutate. Per altre informazioni, vedere destinazione, valutazione.

## <a name="target-running"></a>destinazione, in esecuzione

Una destinazione con una condizione che restituisce false non è in esecuzione, vale a dire che non ha effetto sulla compilazione. Le destinazioni in esecuzione vengono eseguite o ignorate. In entrambi i casi, la destinazione viene valutata. Per altre informazioni, vedere destinazione, valutazione.

## <a name="target-skipping"></a>destinazione, ignorare

Se la compilazione incrementale determina che tutti i file di output sono aggiornati, la destinazione viene ignorata, ovvero viene valutata, ma le attività nella destinazione non vengono eseguite. Per altre informazioni, vedere destinazione, valutazione.

## <a name="target-framework-moniker"></a>moniker framework di destinazione

Nome che descrive il framework (ad esempio, .NETFramework, Silverlight e così via), la versione e il profilo (ad esempio, client, server e così via) che si vogliono specificare come destinazione.

## <a name="targeting-pack"></a>Targeting Pack

Elenco di assembly distribuiti con un determinato framework e set di assembly di riferimento per tale framework.

## <a name="targets-file"></a>file di destinazioni

Un file di destinazioni è un file di progetto contenente principalmente destinazioni e attività che forniscono indicazioni per la compilazione. Per convenzione, l'estensione di file è *targets*. I file di destinazione vengono in genere importati alla fine dei file di progetto associati.

## <a name="task"></a>attività

Le attività sono unità di codice eseguibile che MSBuild i progetti usano per eseguire operazioni di compilazione. Ad esempio, un'attività potrebbe compilare file di input o eseguire uno strumento esterno. Per altre informazioni, vedere [Tasks](../msbuild/msbuild-tasks.md) (Attività).

## <a name="transform"></a>trasformazione

Una trasformazione è una conversione uno a uno di una raccolta di elementi in un'altra. Oltre a consentire a un progetto di convertire le raccolte di elementi, una trasformazione consente a una destinazione di identificare un mapping diretto tra gli input e gli output. Per altre informazioni, vedere [Trasformazioni](../msbuild/msbuild-transforms.md).

## <a name="well-known-metadata"></a>metadati noti

Vedere *metadati, noti*.

## <a name="see-also"></a>Vedi anche

- [MSBuild](../msbuild/msbuild.md)
