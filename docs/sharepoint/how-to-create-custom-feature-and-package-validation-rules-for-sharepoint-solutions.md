---
title: Creare convalide di funzionalità e pacchetti per SharePoint soluzioni
titleSuffix: ''
description: Creare regole di convalida personalizzate per verificare il pacchetto della soluzione generato Visual Studio o per verificare un'intera funzionalità.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: a8cf9b5aa392e04865b0755fdc7dc8933c77bac1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135897"
---
# <a name="create-feature-and-package-validations-for-sharepoint-solutions"></a>Creare convalide di funzionalità e pacchetti per SharePoint soluzioni

  È possibile creare regole di convalida personalizzate per verificare il pacchetto della soluzione generato da Visual Studio. È possibile eseguire la convalida completa su un'intera funzionalità o pacchetto selezionando **Convalida** dal menu di scelta rapida di un pacchetto o di una funzionalità in **PackagingExplorer**. La convalida parziale viene eseguita quando si aggiungono nuovi elementi SharePoint progetto o funzionalità al progetto per determinare se lo stato del pacchetto o della funzionalità è valido.

### <a name="to-create-a-custom-package-validation-rule"></a>Per creare una regola di convalida del pacchetto personalizzata

1. Creare un progetto Libreria di classi.

2. Aggiungere riferimenti agli assembly riportati di seguito:

    - Microsoft.VisualStudio. SharePoint

    - System.ComponentModel.Composition

3. Creare una classe che implementa una delle interfacce seguenti:

    - Per creare una regola di convalida del pacchetto, implementare <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> l'interfaccia .

    - Per creare una regola di convalida della funzionalità, implementare <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> l'interfaccia .

4. Aggiungere alla <xref:System.ComponentModel.Composition.ExportAttribute> classe . Questo attributo consente Visual Studio individuare e caricare la regola di convalida. Passare il <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> tipo o al costruttore <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> dell'attributo.

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato come creare una regola di convalida della funzionalità personalizzata.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb" id="Snippet1":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede riferimenti agli assembly seguenti:

- Microsoft.VisualStudio. SharePoint.

- System.componentmodel.composition.

## <a name="deploy-the-extension"></a>Distribuzione dell'estensione
 Per distribuire l'estensione, creare un pacchetto di estensione (VSIX) per l'assembly e tutti gli altri file che [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] si desidera distribuire con l'estensione. Per altre informazioni, vedere [Deploy Extensions for the SharePoint tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche
- [Estendere SharePoint creazione di pacchetti e distribuzione](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
