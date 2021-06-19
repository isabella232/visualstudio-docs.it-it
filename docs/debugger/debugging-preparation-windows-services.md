---
title: Preparare il debug dei servizi Windows | Microsoft Docs
description: Preparare il debug dei servizi windows, ovvero programmi eseguiti in background in Windows, in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Windows services
- Windows Service applications, debugging
ms.assetid: ac0a99f7-ec3d-4a20-b17f-698a817fdcc2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 01448fcd477f5b17b78ad2b142b965f30798746b
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387736"
---
# <a name="debugging-preparation-windows-services"></a>Preparazione al debug: servizi Windows
Un servizio Windows è un programma che viene eseguito in background in Microsoft Windows. Ne sono un esempio il servizio Telnet e il Time Service di Windows che aggiorna l'orologio visualizzato sul computer. I servizi Windows non possono essere eseguiti dall'interno di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. L'esecuzione deve avvenire nel contesto di Gestione controllo servizi. Per altre informazioni, vedere [Creare servizi Windows](/dotnet/framework/windows-services/how-to-create-windows-services), [Eseguire il debug di applicazioni di servizio per Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications) e [Applicazioni di servizi Windows](/dotnet/framework/windows-services/index).

## <a name="see-also"></a>Vedi anche
- [Debug del codice gestito](../debugger/debugging-managed-code.md)
- [Tipi di progetto C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Impostazioni di progetto per le configurazioni di debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Impostazioni di progetto per una configurazione Visual Basic debug](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Procedura: Eseguire il debug del metodo OnStart](../debugger/how-to-debug-the-onstart-method.md)