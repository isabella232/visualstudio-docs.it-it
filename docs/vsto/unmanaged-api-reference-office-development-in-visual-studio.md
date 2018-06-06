---
title: Riferimenti alle API non gestite (sviluppo per Office in Visual Studio)
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, reference
- Office development in Visual Studio, unmanaged API reference
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 97388073d63b25bb17a7f49f4e2c5fb96bf2f572
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767897"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Riferimenti alle API non gestite (sviluppo per Office in Visual Studio)
  A partire da Microsoft Office system 2007, le applicazioni Office usano il [interfaccia IManagedAddin](../vsto/imanagedaddin-interface.md) interfaccia per chiamare un componente aggiuntivo VSTO del caricatore di componenti che è incluso il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Questo componente viene usato per consentire il caricamento dei componenti aggiuntivi VSTO gestiti. Implementando questa interfaccia, è possibile creare il proprio componente di caricamento di componenti aggiuntivi VSTO.  
  
> [!NOTE]  
>  Interessati allo sviluppo di soluzioni che estendono l'esperienza di Office in [più piattaforme](https://dev.office.com/add-in-availability)? Vedere la nuova [modello aggiuntivi di Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Componenti aggiuntivi di Office hanno un footprint ridotto rispetto alle soluzioni e i componenti aggiuntivi VSTO e possono essere creati con quasi tutte le tecnologie, ad esempio HTML5, JavaScript, CSS3 e XML di programmazione web.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Interfaccia IManagedAddin](../vsto/imanagedaddin-interface.md)  
 Un'interfaccia COM che è possibile implementare per caricare e scaricare componenti aggiuntivi VSTO gestiti nelle applicazioni di Office.  
  
  