---
title: Eseguire il debug Interface Access SDK | Microsoft Docs
ms.date: 07/24/2018
ms.topic: conceptual
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
ms.openlocfilehash: 915f594a984af41da167e0fd3d58beb2f6ddd978
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56608084"
---
# <a name="debug-interface-access-sdk"></a>Debug Interface Access SDK

Il Microsoft eseguire il Debug dell'interfaccia Access Software Development Kit (DIA SDK) fornisce l'accesso alle informazioni archiviate nei file di programma del database (con estensione pdb) generati dagli strumenti di post-compilazione di Microsoft di debug. Poiché il formato del file PDB generato dagli strumenti di post-compilazione sottoposto a revisione costante, che espone il formato è poco pratico. Usando l'API di DIA, è possibile sviluppare applicazioni che cercano ed esplorare le informazioni di debug archiviate in un file con estensione pdb. Tali applicazioni potrebbe, ad esempio, segnalare informazioni sullo stack di traccia-back e analizzare i dati sulle prestazioni.

## <a name="in-this-section"></a>Contenuto della sezione

[Introduzione](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)

Fornisce una panoramica di DIA SDK le funzionalità e specifica in cui è installato il DIA SDK, nonché i file di libreria e intestazione obbligatoria.

[Esecuzione di query nel file PDB](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)

Vengono fornite istruzioni su come usare l'API di DIA per eseguire query sul file con estensione pdb.

[Simboli e relativi tag](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)

Viene descritto come vengono usati i simboli e relativi tag nell'API di DIA.

[Riferimento](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)

Contiene le interfacce, metodi, le enumerazioni e strutture dell'API di DIA.

[Esempio Dia2dump](../../debugger/debug-interface-access/dia2dump-sample.md)

Viene illustrato come usare l'API di DIA per cercare ed esplorare le informazioni di debug.
