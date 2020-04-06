---
title: 'Procedura: utilizzare elementi colorabili incorporati Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34e07894c3306f544396e53001990f7b9a2df5a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707780"
---
# <a name="how-to-use-built-in-colorable-items"></a>Procedura: Utilizzare elementi colorabili incorporatiHow to: Use built-in colorable items
Prima di utilizzare gli elementi colorabili incorporati, è necessario innanzitutto segnalare all'ambiente di sviluppo integrato (IDE) che <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> non si forniscono elementi colorabili personalizzati, che in questo caso sarebbero oggetti. A tale scopo, impostare una voce del Registro di sistema per il servizio di linguaggio.

## <a name="to-use-built-in-colorable-items"></a>Per utilizzare gli elementi colorabili incorporati

1. Nella **sezione HKEY_LOCAL_MACHINE,\\ VisualStudio<X.Y,>, lingue, Servizi\\ di\>** linguaggio \<<nome della lingua , dove \<> X.Y è una versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e Nome lingua> è il nome della lingua, creare un valore della voce del Registro di sistema DWORD denominato **RequestStockColors**.

2. Impostare il valore della voce del Registro di sistema **RequestStockColors** su *1*.

    Dopo aver creato la voce del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Registro di sistema, <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> il metodo del colorizer può utilizzare i membri dell'enumerazione per compilare la matrice di attributi di colore per l'utilizzo da parte dell'editor.

   > [!NOTE]
   > Non impostare questa voce del Registro di sistema se si forniscono elementi colorabili personalizzati. Per ulteriori informazioni, consultate [Elementi colorabili personalizzati.](../../extensibility/internals/custom-colorable-items.md)

## <a name="see-also"></a>Vedere anche
- [Colorazione della sintassi negli editor personalizzati](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementazione della colorazione della sintassiImplementing syntax coloring](../../extensibility/internals/implementing-syntax-coloring.md)
- [Elementi colorabili personalizzati](../../extensibility/internals/custom-colorable-items.md)
- [Registrare un servizio di linguaggio legacyRegister a legacy language service](../../extensibility/internals/registering-a-legacy-language-service2.md)
