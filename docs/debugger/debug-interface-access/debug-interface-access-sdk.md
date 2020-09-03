---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da0ced56e8bf7e61e7fa5251e834a762d4c66650
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468693"
---
# <a name="debug-interface-access-sdk"></a>Debug Interface Access SDK

Microsoft Debug Interface Access Software Development Kit (DIA SDK) fornisce l'accesso alle informazioni di debug archiviate nei file di database di programma (con estensione pdb) generati dagli strumenti di Microsoft postcompiler. Poiché il formato del file con estensione PDB generato dagli strumenti del postcompilatore subisce una revisione costante, l'esposizione del formato non è praticabile. Utilizzando l'API DIA è possibile sviluppare applicazioni che consentono di cercare ed esplorare le informazioni di debug archiviate in un file con estensione pdb. Tali applicazioni potrebbero, ad esempio, ottenere informazioni sulla traccia dello stack e analizzare i dati sulle prestazioni.

## <a name="in-this-section"></a>Contenuto della sezione

[Per iniziare](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)

Fornisce una panoramica delle funzionalità di DIA SDK e specifica la posizione in cui è installato il DIA SDK nonché i file di intestazione e di libreria necessari.

[Esecuzione di query nel file PDB](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)

Fornisce istruzioni su come usare l'API DIA per eseguire una query sul file con estensione pdb.

[Simboli e relativi tag](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)

Viene illustrato come usare simboli e tag di simboli nell'API DIA.

[Riferimento](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)

Contiene le interfacce, i metodi, le enumerazioni e le strutture dell'API DIA.

[Esempio Dia2dump](../../debugger/debug-interface-access/dia2dump-sample.md)

Viene illustrato come usare l'API DIA per cercare e visualizzare le informazioni di debug.
