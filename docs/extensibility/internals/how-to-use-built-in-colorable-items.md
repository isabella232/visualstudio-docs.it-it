---
title: 'Procedura: Usare elementi colorabili incorporati | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f0900792b92a185ce7da66440e0b368870e97be
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54965955"
---
# <a name="how-to-use-built-in-colorable-items"></a>Procedura: Usare elementi colorabili incorporati
Prima di usare gli elementi colorabili incorporati, è necessario prima segnalare all'ambiente di sviluppo integrato (IDE) che non si specifica i proprio elementi colorabili personalizzati, che in questo caso sarebbe <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> oggetti. Eseguire questa operazione impostando una voce del Registro di sistema per il servizio di linguaggio.  
  
## <a name="to-use-built-in-colorable-items"></a>Usare elementi colorabili incorporati  
  
1. Sotto **HKEY_LOCAL_MACHINE\VisualStudio\\< x. y > \Languages\Language Services\\< nome lingua\>**, dove \<x. y > è una versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e \<Nome linguaggio > è il nome del linguaggio, di creare un valore di voce del Registro di sistema valore DWORD denominato **RequestStockColors**.  
  
2. Impostare il **RequestStockColors** al valore della voce del Registro di sistema *1*.  
  
    Dopo aver creato il Registro di sistema, il colorizzatore della voce <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo può usare i membri del <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> enumerazione da inserire nella matrice di attributi di colore da utilizzare dall'editor.  
  
   > [!NOTE]
   >  Non impostare questa voce del Registro di sistema se si fornisce elementi colorabili personalizzati. Per altre informazioni, vedere [elementi colorabili personalizzati](../../extensibility/internals/custom-colorable-items.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Colorazione della sintassi negli editor personalizzati](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementazione della colorazione della sintassi](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Elementi colorabili personalizzati](../../extensibility/internals/custom-colorable-items.md)   
 [Registrare un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service2.md)