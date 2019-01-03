---
title: Riferimenti alle API non gestite (sviluppo per Office in Visual Studio)
ms.date: 02/02/2017
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
ms.openlocfilehash: 1ac4dfa9dd697993cffb527be521bd04c4c087ca
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53991162"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Riferimenti alle API non gestite (sviluppo per Office in Visual Studio)
  A partire da Microsoft Office system 2007, utilizzano le applicazioni di Office il [interfaccia IManagedAddin](../vsto/imanagedaddin-interface.md) interfaccia da chiamare in un componente aggiuntivo VSTO caricatore incluso con il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Questo componente viene usato per consentire gestiti caricamento componenti aggiuntivi VSTO. Implementando questa interfaccia, è possibile creare il proprio componente di caricamento di componenti aggiuntivi VSTO.  
  
> [!NOTE]  
>  Se ti interessa sviluppare soluzioni che estendono l'esperienza di Office attraverso [piattaforme multiple](https://dev.office.com/add-in-availability)? Consultare la nuova [modello di componenti aggiuntivi di Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Componenti aggiuntivi di Office con footprint ridotto rispetto alle soluzioni e componenti aggiuntivi VSTO e si possono essere compilate usando praticamente qualsiasi tecnologia, ad esempio HTML5, JavaScript, CSS3 e XML di programmazione web.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [IManagedAddin (interfaccia)](../vsto/imanagedaddin-interface.md)  
 Un'interfaccia COM che è possibile implementare per caricare e scaricare componenti aggiuntivi VSTO gestiti nelle applicazioni di Office.  
