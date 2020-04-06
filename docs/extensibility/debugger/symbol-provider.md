---
title: 'Provider di simboli : Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31b90846d9494ee046cf9dc4a3e5de9ff033ea3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712816"
---
# <a name="symbol-provider"></a>Provider di simboli
Un'implementazione dell'analizzatore di espressioni deve accedere alle informazioni di debug simboliche generate dal compilatore di linguaggio per valutare variabili ed espressioni. A tale scopo, utilizza le interfacce di un provider di simboli (SP), denominato anche gestore di simboli.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fornisce GLI SP per il codice gestito e il codice nativo utilizzando il formato di file di simboli PDB (Program DataBase). A meno che non vi sia una forte necessità per il programma di utilizzare i simboli [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]memorizzati in un formato personalizzato, si consiglia di utilizzare gli SP forniti da .

## <a name="implementation-notes"></a>Note sull'implementazione
 I [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] motori di debug prevedono di comunicare con gli SP utilizzando le interfacce CLR (Common Language Runtime). Di conseguenza, un SP che funzionerà con i motori di debug di Visual Studio deve supportare CLR. Un elenco completo di tutte le interfacce di debug CLR è [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]disponibile in debugref.doc, che fa parte di .

 Se il tuo SP funzionerà solo con il motore di debug personalizzato, puoi implementare il SP come meglio credi a seconda delle esigenze del motore di debug.

## <a name="see-also"></a>Vedere anche
- [Componenti del debugger](../../extensibility/debugger/debugger-components.md)
