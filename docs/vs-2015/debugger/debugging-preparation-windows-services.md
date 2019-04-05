---
title: 'Debug della preparazione: Servizi di Windows | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
helpviewer_keywords:
- debugging [Visual Studio], Windows services
- Windows Service applications, debugging
ms.assetid: ac0a99f7-ec3d-4a20-b17f-698a817fdcc2
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3d18dcf94c9dd1223446e55025465d1a3b455526
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58967290"
---
# <a name="debugging-preparation-windows-services"></a>Debug della preparazione: servizi Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un servizio Windows è un programma che viene eseguito in background in Microsoft Windows. Ne sono un esempio il servizio Telnet e il Time Service di Windows che aggiorna l'orologio visualizzato sul computer. I servizi Windows non possono essere eseguiti dall'interno di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. L'esecuzione deve avvenire nel contesto di Gestione controllo servizi. Per altre informazioni, vedere [Creare servizi Windows](http://msdn.microsoft.com/library/0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff), [Eseguire il debug di applicazioni di servizio per Windows](http://msdn.microsoft.com/library/63ab0800-0f05-4f1e-88e6-94c73fd920a2) e [Applicazioni di servizi Windows](http://msdn.microsoft.com/library/ba72d648-9553-4849-b829-069ad5ea014b).  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di codice gestito](../debugger/debugging-managed-code.md)   
 [Tipi di progetto C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Impostazioni di progetto per le configurazioni di debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Impostazioni di progetto per una configurazione di debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Procedura: Eseguire il debug del metodo OnStart](../debugger/how-to-debug-the-onstart-method.md)
