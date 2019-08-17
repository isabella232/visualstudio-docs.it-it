---
title: Riferimenti alle API non gestite (sviluppo per Office in Visual Studio)
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, reference
- Office development in Visual Studio, unmanaged API reference
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 00db78359154dbda600fb4b58103bc04e89d16b2
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551319"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Riferimenti alle API non gestite (sviluppo per Office in Visual Studio)

A partire dal sistema di Microsoft Office 2007, le applicazioni di Office usano l'interfaccia dell' [interfaccia IManagedAddin](../vsto/imanagedaddin-interface.md) per chiamare un componente del caricatore di componenti aggiuntivi VSTO incluso [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]in. Questo componente viene usato per consentire il caricamento di componenti aggiuntivi VSTO gestiti. Implementando questa interfaccia, è possibile creare il proprio componente di caricamento di componenti aggiuntivi VSTO.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>Contenuto della sezione

[Interfaccia IManagedAddin](../vsto/imanagedaddin-interface.md)

Un'interfaccia COM che è possibile implementare per caricare e scaricare componenti aggiuntivi VSTO gestiti nelle applicazioni di Office.
