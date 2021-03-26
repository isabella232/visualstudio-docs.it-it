---
title: Provider di simboli | Microsoft Docs
description: Informazioni sui provider di simboli forniti da Visual Studio per consentire a un analizzatore di espressioni di valutare variabili ed espressioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 132e3c15eed86c9008e49b74b6da6e5da5a3ce33
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079384"
---
# <a name="symbol-provider"></a>Provider di simboli
Un'implementazione dell'analizzatore di espressioni deve accedere alle informazioni di debug simboliche generate dal compilatore del linguaggio per valutare variabili ed espressioni. Questa operazione viene eseguita tramite l'utilizzo delle interfacce di un provider di simboli (SP), denominato anche gestore di simboli.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce SPs per codice gestito e codice nativo utilizzando il formato di file di simboli del DataBase di programma (PDB). A meno che non sia necessario che il programma usi i simboli archiviati in un formato personalizzato, è consigliabile usare SPs fornito da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="implementation-notes"></a>Note sull'implementazione
 I [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] motori di debug si aspettano di comunicare con SPS usando le interfacce CLR (Common Language Runtime). Di conseguenza, un SP che lavorerà con i motori di debug di Visual Studio deve supportare CLR. Un elenco completo di tutte le interfacce di debug CLR si trova in debugref.doc, che fa parte di [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] .

 Se il servizio SP funziona solo con il motore di debug personalizzato, è possibile implementare SP in base alle esigenze del motore di debug.

## <a name="see-also"></a>Vedi anche
- [Componenti del debugger](../../extensibility/debugger/debugger-components.md)
