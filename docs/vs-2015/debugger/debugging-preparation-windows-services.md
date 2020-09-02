---
title: 'Preparazione al debug: Servizi Windows | Microsoft Docs'
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
ms.openlocfilehash: 2e68792b62e3e5538476063b5298579ecc58e4db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691310"
---
# <a name="debugging-preparation-windows-services"></a>Preparazione al debug: servizi Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un servizio Windows è un programma che viene eseguito in background in Microsoft Windows. Ne sono un esempio il servizio Telnet e il Time Service di Windows che aggiorna l'orologio visualizzato sul computer. I servizi Windows non possono essere eseguiti dall'interno di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. L'esecuzione deve avvenire nel contesto di Gestione controllo servizi. Per altre informazioni, vedere [Creare servizi Windows](https://msdn.microsoft.com/library/0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff), [Eseguire il debug di applicazioni di servizio per Windows](https://msdn.microsoft.com/library/63ab0800-0f05-4f1e-88e6-94c73fd920a2) e [Applicazioni di servizi Windows](https://msdn.microsoft.com/library/ba72d648-9553-4849-b829-069ad5ea014b).  
  
## <a name="see-also"></a>Vedere anche  
 [Debug del codice gestito](../debugger/debugging-managed-code.md)   
 [Tipi di progetto C#, F # e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Impostazioni di progetto per le configurazioni di debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Impostazioni di progetto per una configurazione di debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Procedura: eseguire il debug del metodo OnStart](../debugger/how-to-debug-the-onstart-method.md)
