---
title: 'Soluzioni SharePoint: creare funzionalità personalizzate, regole di convalida del pacchetto'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: f731b6af2ada8caddb84be5561d7f6dc304e7bbd
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016905"
---
# <a name="how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions"></a>Procedura: creare regole personalizzate per la convalida di funzionalità e pacchetti per le soluzioni SharePoint
  È possibile creare regole di convalida personalizzate per verificare il pacchetto della soluzione generato da Visual Studio. È possibile eseguire la convalida completa su un'intera funzionalità o un pacchetto selezionando **convalida** dal menu di scelta rapida di un pacchetto o di una funzionalità in **PackagingExplorer**. La convalida parziale viene eseguita quando si aggiungono nuove funzionalità o elementi del progetto SharePoint al progetto per determinare se il pacchetto o la funzionalità sono in uno stato valido.

### <a name="to-create-a-custom-package-validation-rule"></a>Per creare una regola di convalida del pacchetto personalizzata

1. Creare un progetto Libreria di classi.

2. Aggiungere riferimenti agli assembly riportati di seguito:

    - Microsoft. VisualStudio. SharePoint

    - System.ComponentModel.Composition

3. Creare una classe che implementi una delle interfacce seguenti:

    - Per creare una regola di convalida del pacchetto, implementare l' <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> interfaccia.

    - Per creare una regola di convalida della funzionalità, implementare l' <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> interfaccia.

4. Aggiungere alla <xref:System.ComponentModel.Composition.ExportAttribute> classe. Questo attributo consente a Visual Studio di individuare e caricare la regola di convalida. Passare il <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> tipo o al costruttore dell'attributo.

## <a name="example"></a>Esempio
 Nell'esempio di codice riportato di seguito viene illustrato come creare una regola di convalida della funzionalità personalizzata.

 [!code-vb[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb#1)]
 [!code-csharp[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs#1)]

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede riferimenti agli assembly seguenti:

- Microsoft. VisualStudio. SharePoint.

- System. ComponentModel. Composition.

## <a name="deploy-the-extension"></a>Distribuzione dell'estensione
 Per distribuire l'estensione, creare un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacchetto di estensione (VSIX) per l'assembly e qualsiasi altro file che si vuole distribuire con l'estensione. Per ulteriori informazioni, vedere la pagina relativa alla [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedere anche
- [Estensione della creazione di pacchetti e della distribuzione di SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
