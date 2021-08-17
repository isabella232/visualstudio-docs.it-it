---
title: Informazioni di riferimento sulle API non gestite (Office sviluppo in Visual Studio)
description: Il riferimento all'API non gestita viene usato per consentire il caricamento di componenti VSTO componenti aggiuntivi. È anche possibile creare il proprio VSTO del caricatore del componente aggiuntivo implementando questa interfaccia.
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
ms.openlocfilehash: 05a8e1bef15e9299c16fccb39705f45f810e1d8bcfb0b16f99aab9b82ae29708
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121226115"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Informazioni di riferimento sulle API non gestite (Office sviluppo in Visual Studio)

A partire dal sistema Microsoft Office 2007, le applicazioni Office usano l'interfaccia [IManagedAddin](../vsto/imanagedaddin-interface.md) per chiamare in un componente caricatore del componente aggiuntivo VSTO incluso in [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Questo componente viene usato per facilitare il caricamento dei componenti VSTO componenti aggiuntivi. È possibile creare il proprio VSTO del caricatore del componente aggiuntivo implementando questa interfaccia.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>Contenuto della sezione

[Interfaccia IManagedAddin](../vsto/imanagedaddin-interface.md)

Un'interfaccia COM che è possibile implementare per caricare e scaricare componenti aggiuntivi VSTO gestiti nelle applicazioni di Office.
