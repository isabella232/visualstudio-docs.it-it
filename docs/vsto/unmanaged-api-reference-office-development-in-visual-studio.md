---
title: Riferimenti alle API non gestite (sviluppo per Office in Visual Studio)
description: Il riferimento all'API non gestita viene usato per aiutare i componenti aggiuntivi VSTO gestiti dal caricamento. È anche possibile creare un componente del caricatore del componente aggiuntivo VSTO implementando questa interfaccia.
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
ms.workload:
- office
ms.openlocfilehash: cac9e2d01b47e0088543aeabcaeff30853314157
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908558"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Riferimenti alle API non gestite (sviluppo per Office in Visual Studio)

A partire dal sistema di Microsoft Office 2007, le applicazioni di Office usano l'interfaccia dell' [interfaccia IManagedAddin](../vsto/imanagedaddin-interface.md) per chiamare un componente del caricatore di componenti aggiuntivi VSTO incluso in [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Questo componente viene usato per consentire il caricamento di componenti aggiuntivi VSTO gestiti. È possibile creare un componente del caricatore del componente aggiuntivo VSTO implementando questa interfaccia.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>Contenuto della sezione

[Interfaccia IManagedAddin](../vsto/imanagedaddin-interface.md)

Un'interfaccia COM che è possibile implementare per caricare e scaricare componenti aggiuntivi VSTO gestiti nelle applicazioni di Office.
