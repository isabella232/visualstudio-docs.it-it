---
title: Eseguire il debug Interface Access SDK | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 319c509ac293b4f55ab574a5f29cdbd23709ebaa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517090"
---
# <a name="debug-interface-access-sdk"></a>Debug Interface Access SDK
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Debug Interface Access SDK](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk).  
  
Il Microsoft eseguire il Debug dell'interfaccia Access Software Development Kit (DIA SDK) fornisce l'accesso alle informazioni archiviate nei file di programma del database (con estensione pdb) generati dagli strumenti di post-compilazione di Microsoft di debug. Poiché il formato del file PDB generato dagli strumenti di post-compilazione sottoposto a revisione costante, che espone il formato è poco pratico. Usando l'API di DIA, è possibile sviluppare applicazioni che cercano ed esplorare le informazioni di debug archiviate in un file con estensione pdb. Tali applicazioni potrebbe, ad esempio, segnalare informazioni sullo stack di traccia-back e analizzare i dati sulle prestazioni.  
  
## <a name="in-this-section"></a>In questa sezione  
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
  
 [File di origine Dia2dump.cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)  
 Utilizzato dal codice sorgente [esempio Dia2dump](../../debugger/debug-interface-access/dia2dump-sample.md) per dimostrare l'API di DIA.



