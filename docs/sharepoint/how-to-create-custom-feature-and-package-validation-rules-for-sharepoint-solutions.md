---
title: "Procedura: creare funzionalità personalizzate e regole di convalida del pacchetto per le soluzioni SharePoint | Documenti Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
- SharePoint development in Visual Studio, validation rules
ms.assetid: 17e818f8-0f3a-4a96-a6fc-1634ddb4825d
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 20a56a2f6582a08270292cd86cf62a9344d8565f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions"></a>Procedura: Creare regole personalizzate per la convalida di funzionalità e pacchetti per le soluzioni SharePoint
  È possibile creare le regole di convalida personalizzata per verificare il pacchetto della soluzione generato da Visual Studio. È possibile eseguire la convalida completa in un'intera funzionalità o un pacchetto selezionando **convalida** dal menu di scelta rapida di un pacchetto o una funzionalità di **PackagingExplorer**. Quando si aggiungono nuovi elementi di progetto SharePoint o una funzionalità al progetto per determinare se il pacchetto o la funzionalità in uno stato valido, viene eseguita la convalida parziale.  
  
### <a name="to-create-a-custom-package-validation-rule"></a>Per creare una regola di convalida del pacchetto personalizzato  
  
1.  Creare un progetto Libreria di classi.  
  
2.  Aggiungere riferimenti agli assembly riportati di seguito:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Creare una classe che implementa una delle interfacce seguenti:  
  
    -   Per creare una regola di convalida del pacchetto, implementare il <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> interfaccia.  
  
    -   Per creare una regola di convalida di funzionalità, implementare il <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> interfaccia.  
  
4.  Aggiungere il <xref:System.ComponentModel.Composition.ExportAttribute> alla classe. Questo attributo consente a Visual Studio di individuare e caricare la regola di convalida. Passare il <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> o <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> tipo al costruttore dell'attributo.  
  
## <a name="example"></a>Esempio  
 Esempio di codice riportato di seguito viene illustrato come creare una regola di convalida di funzionalità personalizzata.  
  
 [!code-vb[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb#1)]
 [!code-csharp[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs#1)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 Questo esempio richiede riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint.  
  
-   System.  
  
## <a name="deploying-the-extension"></a>Distribuzione dell'estensione  
 Per distribuire l'estensione, creare un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) per l'assembly e altri file che si desiderano distribuire con l'estensione del pacchetto. Per ulteriori informazioni, vedere [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione della creazione di pacchetti e della distribuzione di SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  