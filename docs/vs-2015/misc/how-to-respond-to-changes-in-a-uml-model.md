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
ms.openlocfilehash: 9eaaa1406591bc950dbbf95aff8dcd732eef3448
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74293393"
---
# <a name="how-to-respond-to-changes-in-a-uml-model"></a>Procedura: rispondere alle modifiche in un modello UML
È possibile scrivere codice che viene eseguito ogni volta che si verifica una modifica in un modello UML in Visual Studio. Il codice risponderà allo stesso modo alle modifiche apportate direttamente dall'utente e a quelle apportate da altre estensioni di Visual Studio. Per informazioni sulle versioni di Visual Studio che supportano modelli UML, vedere [Supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!WARNING]
> Queste tecniche non sono supportate dall'API UML e potrebbero non funzionare nelle prossime versioni di Visual Studio.

## <a name="see-also"></a>Vedere anche
 [Esplorare i gestori eventi del modello UML](../modeling/navigate-the-uml-model.md) [propagare le modifiche al di fuori dell'](../modeling/event-handlers-propagate-changes-outside-the-model.md) [esempio di modello: Color by stereotipo](https://go.microsoft.com/fwlink/?LinkId=213841)