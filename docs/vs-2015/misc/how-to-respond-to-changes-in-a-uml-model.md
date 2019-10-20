---
title: 'Procedura: rispondere alle modifiche in un modello UML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: f0300371-9cac-4def-a3f5-7d7b62dcd6f3
caps.latest.revision: 3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: eff43f3c7547a46b75885448999335637e9fbc62
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609798"
---
# <a name="how-to-respond-to-changes-in-a-uml-model"></a>Procedura: rispondere alle modifiche in un modello UML
È possibile scrivere codice che viene eseguito ogni volta che si verifica una modifica in un modello UML in Visual Studio. Il codice risponderà allo stesso modo alle modifiche apportate direttamente dall'utente e a quelle apportate da altre estensioni di Visual Studio. Per individuare le versioni di Visual Studio che supportano i modelli UML, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!WARNING]
> Queste tecniche non sono supportate dall'API UML e potrebbero non funzionare nelle prossime versioni di Visual Studio.

 Il codice di esempio è disponibile in [UML: rispondere alle modifiche in un modello UML usando eventi e regole](http://code.msdn.microsoft.com/UML-Responding-to-changes-c024cd4b)

## <a name="see-also"></a>Vedere anche
 [Esplorare i gestori eventi del modello UML](../modeling/navigate-the-uml-model.md) [propagare le modifiche al di fuori dell'](../modeling/event-handlers-propagate-changes-outside-the-model.md) [esempio di modello: Color by stereotipo](http://go.microsoft.com/fwlink/?LinkId=213841)