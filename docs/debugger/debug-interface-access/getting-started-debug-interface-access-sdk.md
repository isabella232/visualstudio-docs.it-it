---
description: Debug Interface Access (DIA) SDK fornisce la documentazione di istruzioni e un esempio che illustra come usare l'API DIA.
title: Attività iniziali (Debug Interface Access SDK) | Microsoft Docs
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 4e74262594e23af3819851bcf23d69692fd7d64c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122081698"
---
# <a name="getting-started-debug-interface-access-sdk"></a>Introduzione (Debug Interface Access SDK)
Debug Interface Access (DIA) SDK fornisce la documentazione di istruzioni e un esempio che illustra come usare l'API DIA. Usare le interfacce e i metodi nel DIA SDK per sviluppare applicazioni personalizzate che aprono i file con estensione pdb e dbg e ricercano nel contenuto simboli, valori, attributi, indirizzi e altre informazioni di debug. Questo SDK fornisce anche tabelle di riferimento per le proprietà associate ai simboli presenti nelle applicazioni C++.

 Per usare al meglio DIA SDK, è necessario avere familiarità con quanto segue:

- Linguaggio di programmazione C++

- Programmazione COM

- Visual Studio ide (Integrated Development Environment) per la compilazione degli esempi

  Il DIA SDK viene in genere installato con Visual Studio e il percorso predefinito è *[unità]* \Programmi\Microsoft Visual Studio 9.0\DIA SDK. Come parte dell'installazione, il msdia90.dll, che implementa il DIA SDK, viene registrato automaticamente, quindi è necessario solo includerlo nel programma e collegarsi a `dia2.h` `diaguids.lib` .

  Intestazione: include\dia2.h

  Libreria: lib\diaguids.lib

  DLL: bin\msdia80.dll

  IDL: idl\dia2.idl

## <a name="in-this-section"></a>Contenuto della sezione

[Overview](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)

Esamina l'architettura di base di DIA.

[Esecuzione di query nel file PDB](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)

Fornisce istruzioni dettagliate su come usare l'API DIA per eseguire query su un file con estensione pdb.

## <a name="see-also"></a>Vedi anche

- [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)
