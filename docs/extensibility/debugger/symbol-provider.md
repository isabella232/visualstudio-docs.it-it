---
title: Provider di simboli | Microsoft Docs
description: Informazioni sui provider di simboli forniti Visual Studio per consentire a un analizzatore di espressioni di valutare variabili ed espressioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 49f26713bcda948220fabdefaa62032e10fde8a2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152588"
---
# <a name="symbol-provider"></a>Provider di simboli
Un'implementazione dell'analizzatore di espressioni deve accedere alle informazioni di debug simboliche generate dal compilatore di linguaggio per valutare variabili ed espressioni. A tale scopo, utilizza le interfacce di un provider di simboli ,denominato anche gestore di simboli.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce gli SP per il codice gestito e il codice nativo usando il formato di file di simboli Program DataBase (PDB). A meno che non sia necessario che il programma usi simboli archiviati in un formato personalizzato, è consigliabile usare i provider di servizi forniti da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="implementation-notes"></a>Note sull'implementazione
 I [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] motori di debug prevedono di parlare con gli SP usando le interfacce CLR (Common Language Runtime). Di conseguenza, un SP che funziona con i motori Visual Studio di debug deve supportare CLR. Un elenco completo di tutte le interfacce di debug CLR è disponibile in debugref.doc, che fa parte di [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] .

 Se sp funziona solo con il motore di debug personalizzato, è possibile implementare sp come si può vedere in base alle esigenze del motore di debug.

## <a name="see-also"></a>Vedi anche
- [Componenti del debugger](../../extensibility/debugger/debugger-components.md)
