---
description: Debug Interface Access (DIA) SDK fornisce documentazione didattica e un esempio che illustra come usare l'API DIA.
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
ms.openlocfilehash: bc3ffc7dddab91a674dbdb09cb53556d17b86cca420f2ba02a7f9ac100bcac6a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121345364"
---
# <a name="getting-started-debug-interface-access-sdk"></a>Introduzione (Debug Interface Access SDK)
Debug Interface Access (DIA) SDK fornisce documentazione didattica e un esempio che illustra come usare l'API DIA. Usare le interfacce e i metodi nel DIA SDK per sviluppare applicazioni personalizzate che aprono i file con estensione pdb e dbg e cercano simboli, valori, attributi, indirizzi e altre informazioni di debug nel contenuto. Questo SDK fornisce anche tabelle di riferimento per le proprietà associate ai simboli presenti nelle applicazioni C++.

 Per usare al meglio il DIA SDK, è necessario avere familiarità con quanto segue:

- Linguaggio di programmazione C++

- Programmazione COM

- Visual Studio ambiente di sviluppo integrato (IDE) per la compilazione degli esempi

  Il DIA SDK viene in genere installato con Visual Studio e il percorso predefinito è *[unità]* \Programmi\Microsoft Visual Studio 9.0\DIA SDK. Come parte dell'installazione, il msdia90.dll, che implementa l'DIA SDK, viene registrato automaticamente in modo che tutto ciò che è necessario fare per usarlo è includere nel programma e `dia2.h` collegarsi a `diaguids.lib` .

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
