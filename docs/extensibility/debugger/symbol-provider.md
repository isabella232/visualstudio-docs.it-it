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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626400"
---
# <a name="symbol-provider"></a>Provider di simboli
Un'implementazione dell'analizzatore di espressioni deve accedere alle informazioni di debug simboliche generate dal compilatore di linguaggio per valutare variabili ed espressioni. A tale scopo, utilizza le interfacce di un provider di simboli, chiamato anche gestore di simboli.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce i provider di servizi per il codice gestito e il codice nativo usando il formato di file di simboli Program DataBase (PDB). A meno che il programma non necessiti di usare simboli archiviati in un formato personalizzato, è consigliabile usare i provider di servizi forniti da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="implementation-notes"></a>Note sull'implementazione
 I motori di debug prevedono di usare le interfacce [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] CLR (Common Language Runtime). Di conseguenza, un SP che verrà utilizzato con i motori Visual Studio di debug deve supportare CLR. Un elenco completo di tutte le interfacce di debug CLR è disponibile in debugref.doc, che fa parte di [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] .

 Se sp funziona solo con il motore di debug personalizzato, è possibile implementare sp come si desidera, a seconda delle esigenze del motore di debug.

## <a name="see-also"></a>Vedi anche
- [Componenti del debugger](../../extensibility/debugger/debugger-components.md)
