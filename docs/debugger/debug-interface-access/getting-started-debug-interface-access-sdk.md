---
title: Introduzione (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- .dbg files
- DBG files
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a93225b4bd4180a9ce3389911c2c15d0dbef52ad
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468602"
---
# <a name="getting-started-debug-interface-access-sdk"></a>Introduzione (Debug Interface Access SDK)
L'SDK di debug Interface Access (DIA) fornisce la documentazione di istruzioni e un esempio che illustra come usare l'API DIA. Utilizzare le interfacce e i metodi del DIA SDK per sviluppare applicazioni personalizzate che aprono i file con estensione PDB e DBG ed esegue ricerche nel contenuto per simboli, valori, attributi, indirizzi e altre informazioni di debug. Questo SDK fornisce anche tabelle di riferimento per le proprietà associate ai simboli presenti nelle applicazioni C++.

 Per usare al meglio il DIA SDK, è necessario avere familiarità con quanto segue:

- Linguaggio di programmazione C++

- Programmazione COM

- Visual Studio Integrated Development Environment (IDE) per la compilazione degli esempi

  Il DIA SDK viene in genere installato con Visual Studio e il percorso predefinito è *[unità]* \Programmi\microsoft Visual Studio 9.0 \ DIA SDK. Nell'ambito dell'installazione di, il msdia90.dll, che implementa l'DIA SDK, viene registrato automaticamente in modo da poterlo utilizzare per l'utilizzo, quindi è necessario includere `dia2.h` nel programma e collegarsi a `diaguids.lib` .

  Intestazione: include\dia2.h

  Libreria: lib\diaguids.lib

  DLL: bin\msdia80.dll

  IDL: idl\dia2.idl

## <a name="in-this-section"></a>Contenuto della sezione

[Panoramica](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)

Esamina l'architettura di base di DIA.

[Ricerche nel file PDB](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)

Fornisce istruzioni dettagliate su come usare l'API DIA per eseguire query in un file con estensione pdb.

## <a name="see-also"></a>Vedi anche

- [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)