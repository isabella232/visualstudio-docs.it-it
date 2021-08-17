---
description: Microsoft Debug Interface Access Software Development Kit (DIA SDK) consente di accedere alle informazioni di debug archiviate nei file di database di programma (con estensione pdb) generati dagli strumenti di postcompilatore Microsoft.
title: Debug Interface Access SDK | Microsoft Docs
ms.date: 07/24/2018
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 8cf60e03894f2a2a4c79e0242ef4e7b53d24deba
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122129503"
---
# <a name="debug-interface-access-sdk"></a>Debug Interface Access SDK

Microsoft Debug Interface Access Software Development Kit (DIA SDK) consente di accedere alle informazioni di debug archiviate nei file di database di programma (con estensione pdb) generati dagli strumenti di postcompilatore Microsoft. Poiché il formato del file con estensione pdb generato dagli strumenti postcompilatore viene sottoposto a revisione costante, esporre il formato non è pratico. Usando l'API DIA, è possibile sviluppare applicazioni che ricercano ed esplorano le informazioni di debug archiviate in un file con estensione pdb. Tali applicazioni potrebbero, ad esempio, segnalare informazioni di analisi dello stack e analizzare i dati sulle prestazioni.

## <a name="in-this-section"></a>Contenuto della sezione

[Per iniziare](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)

Offre una panoramica delle funzionalità DIA SDK e specifica dove viene installato il DIA SDK, nonché i file di intestazione e di libreria necessari.

[Esecuzione di query nel file PDB](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)

Fornisce istruzioni su come usare l'API DIA per eseguire query sul file con estensione pdb.

[Simboli e relativi tag](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)

Viene illustrato come vengono usati i simboli e i tag dei simboli nell'API DIA.

[Riferimento](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)

Contiene le interfacce, i metodi, le enumerazioni e le strutture dell'API DIA.

[Esempio Dia2dump](../../debugger/debug-interface-access/dia2dump-sample.md)

Illustra come usare l'API DIA per cercare ed esplorare le informazioni di debug.
