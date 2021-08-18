---
title: Informazioni di riferimento sulle API non gestite (Office sviluppo in Visual Studio)
description: Le informazioni di riferimento sulle API non gestite vengono usate per facilitare il caricamento VSTO componenti aggiuntivi. È anche possibile creare il proprio VSTO del caricatore del componente aggiuntivo implementando questa interfaccia.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 08/14/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, reference
- Office development in Visual Studio, unmanaged API reference
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 132c4ba7286ae04d7e9c64a1a6306fc14b2ea650
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122082738"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Informazioni di riferimento sulle API non gestite (Office sviluppo in Visual Studio)

A partire dal sistema Microsoft Office 2007, le applicazioni Office usano l'interfaccia [IManagedAddin](../vsto/imanagedaddin-interface.md) per chiamare in un componente caricatore del componente aggiuntivo VSTO incluso in [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Questo componente viene usato per facilitare il caricamento VSTO componenti aggiuntivi. È possibile creare il proprio VSTO del caricatore del componente aggiuntivo implementando questa interfaccia.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>Contenuto della sezione

[Interfaccia IManagedAddin](../vsto/imanagedaddin-interface.md)

Un'interfaccia COM che è possibile implementare per caricare e scaricare componenti aggiuntivi VSTO gestiti nelle applicazioni di Office.
