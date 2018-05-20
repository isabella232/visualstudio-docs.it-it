---
title: 'Procedura: le applicazioni di Office di destinazione tramite assembly di interoperabilità primari'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- assemblies [Office development in Visual Studio], PIA references
- primary interop assemblies [Office development in Visual Studio], adding references to
- Office primary interop assemblies in Visual Studio, adding references to
- Office applications [Office development in Visual Studio], automating
- application development [Office development in Visual Studio], automating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 32ff157e3986836ac13472c4a9ed8a7b01f06e04
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="how-to-target-office-applications-through-primary-interop-assemblies"></a>Procedura: le applicazioni di Office di destinazione tramite assembly di interoperabilità primari
  Quando si crea un nuovo progetto di Office, in Visual Studio vengono aggiunti automaticamente riferimenti agli assembly di interoperabilità primari (PIA) di Microsoft Office necessari per la compilazione del progetto. È necessario aggiungere riferimenti agli altri assembly di interoperabilità primari (PIA) negli scenari seguenti:  
  
-   Si vuole usare funzionalità di altre applicazioni di Microsoft Office nel progetto, ad esempio, funzionalità di Microsoft Office Excel in un progetto per Microsoft Office Word.  
  
-   Si vuole automatizzare applicazioni di Microsoft Office prive di progetti dedicati in Visual Studio, ad esempio Microsoft Office Access.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="to-add-a-reference-to-a-primary-interop-assembly"></a>Per aggiungere un riferimento a un assembly di interoperabilità primario  
  
1.  Aprire il progetto di Office e selezionare il nome del progetto in **Esplora**.  
  
2.  Scegliere **Aggiungi riferimento** dal menu **Progetto**.  
  
3.  Nel **Framework** , selezionare l'assembly di interoperabilità primario in cui si desidera il **nome componente** elenco. Per ulteriori informazioni sugli assembly di interoperabilità primari di Microsoft Office disponibili, vedere [assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md).  
  
     Se il progetto è destinato il [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, il **incorpora tipi di interoperabilità** per il riferimento all'assembly è impostata su **True** per impostazione predefinita. Usando questa impostazione, la soluzione non richiede l'assembly di interoperabilità primario (PIA) sui computer degli utenti finali. Per altre informazioni, vedere [progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md).  
  
    > [!NOTE]  
    >  Nei progetti di Office, aggiungere sempre riferimenti agli assembly di interoperabilità primari Office utilizzando il **.NET** scheda della finestra il **Aggiungi riferimento** finestra di dialogo anziché **COM** scheda. Per altre informazioni, vedere [assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md).  
  
4.  Fare clic su **OK**.  
  
     Viene visualizzato il nome di assembly di **riferimenti** cartella di **Esplora**.  
  
## <a name="see-also"></a>Vedere anche  
 [Assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md)   
 [Scrivere il codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)   
 [Lo sviluppo di soluzioni Office](../vsto/developing-office-solutions.md)   
 [Procedura: assembly di interoperabilità primari di installazione di Office](../vsto/how-to-install-office-primary-interop-assemblies.md)  
  
  