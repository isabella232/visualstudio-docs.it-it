---
title: 'Procedura: Creare funzionalità personalizzate e regole di convalida del pacchetto per le soluzioni SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
- SharePoint development in Visual Studio, validation rules
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 794974991216a521bf2ca4afb1e958716a3bf735
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874081"
---
# <a name="how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions"></a>Procedura: Creare pacchetti di funzionalità personalizzate le regole di convalida per le soluzioni SharePoint
  È possibile creare le regole di convalida personalizzata per verificare il pacchetto della soluzione generato da Visual Studio. È possibile eseguire la convalida completa in un'intera funzione o un pacchetto selezionando **Validate** dal menu di scelta rapida di un pacchetto o una funzionalità nel **PackagingExplorer**. Quando si aggiungono nuovi elementi di progetto SharePoint o le funzionalità al progetto per determinare se il pacchetto o la funzionalità sarà in uno stato valido, viene eseguita la convalida parziale.  
  
### <a name="to-create-a-custom-package-validation-rule"></a>Per creare una regola di convalida pacchetto personalizzato  
  
1.  Creare un progetto Libreria di classi.  
  
2.  Aggiungere riferimenti agli assembly riportati di seguito:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Creare una classe che implementa una delle interfacce seguenti:  
  
    -   Per creare una regola di convalida del pacchetto, implementare il <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> interfaccia.  
  
    -   Per creare una regola di convalida di funzionalità, implementare il <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> interfaccia.  
  
4.  Aggiungere il <xref:System.ComponentModel.Composition.ExportAttribute> alla classe. Questo attributo consente a Visual Studio di individuare e caricare la regola di convalida. Passare il <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> o <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> tipo al costruttore dell'attributo.  
  
## <a name="example"></a>Esempio  
 Esempio di codice seguente viene illustrato come creare una regola di convalida di funzionalità personalizzata.  
  
 [!code-vb[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb#1)]
 [!code-csharp[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs#1)]  
  
## <a name="compile-the-code"></a>Compilare il codice  
 In questo esempio vengono richiesti riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint.  
  
-   System.ComponentModel.Composition.  
  
## <a name="deploy-the-extension"></a>Distribuire l'estensione  
 Per distribuire l'estensione, creare un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) creare un pacchetto per l'assembly e qualsiasi altro file che si desidera distribuire con l'estensione. Per altre informazioni, vedere [gli strumenti di distribuzione di estensioni per SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vedere anche
 [Estendere la distribuzione e creazione di pacchetti di SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
