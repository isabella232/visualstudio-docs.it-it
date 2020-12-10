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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 043014ebababd990c9cae03f28cb1b642d576071
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996045"
---
# <a name="symbol-provider"></a>Provider di simboli
Un'implementazione dell'analizzatore di espressioni deve accedere alle informazioni di debug simboliche generate dal compilatore del linguaggio per valutare variabili ed espressioni. Questa operazione viene eseguita tramite l'utilizzo delle interfacce di un provider di simboli (SP), denominato anche gestore di simboli.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce SPs per codice gestito e codice nativo utilizzando il formato di file di simboli del DataBase di programma (PDB). A meno che non sia necessario che il programma usi i simboli archiviati in un formato personalizzato, è consigliabile usare SPs fornito da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="implementation-notes"></a>Note sull'implementazione
 I [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] motori di debug si aspettano di comunicare con SPS usando le interfacce CLR (Common Language Runtime). Di conseguenza, un SP che lavorerà con i motori di debug di Visual Studio deve supportare CLR. Un elenco completo di tutte le interfacce di debug CLR si trova in debugref.doc, che fa parte di [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] .

 Se il servizio SP funziona solo con il motore di debug personalizzato, è possibile implementare SP in base alle esigenze del motore di debug.

## <a name="see-also"></a>Vedere anche
- [Componenti del debugger](../../extensibility/debugger/debugger-components.md)
