---
title: "Procedura: Creare modelli di elementi a più file | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
ms.assetid: fe3c4257-e383-4c80-b8af-c5c521959c33
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a0cdd8fdd8ec36ccb070e8aaa197d728047a3fef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-multi-file-item-templates"></a>Procedura: creare modelli di elementi a più file
Sebbene i modelli di elementi possano specificare un solo elemento, in alcuni casi l'elemento è costituito da più file. Ad esempio, un modello di elemento di Windows Forms per Visual Basic richiede i tre file seguenti:  
  
-   Un file con estensione vb che contiene il codice per il modulo.  
  
-   Un file designer.vb che contiene le informazioni della finestra di progettazione del modulo.  
  
-   Un file con estensione resx che contiene le risorse incorporate del modulo.  
  
 Per i modelli di elementi a più file è necessario specificare i parametri per assicurarsi che vengano usate le estensioni dei nomi di file corrette quando l'elemento viene creato in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Se si crea un modello di elemento usando l'**Esportazione guidata modelli**, questi parametri vengono generati automaticamente e non è richiesta alcuna ulteriore modifica. La procedura seguente descrive come usare i parametri per assicurarsi che vengano create le estensioni dei nomi di file corrette.  
  
### <a name="to-manually-create-a-multi-file-item-template"></a>Per creare manualmente un modello di elemento a più file  
  
1.  Creare il modello di elemento allo stesso modo in cui si crea un modello di elemento a file singolo. Per altre informazioni, vedere [Procedura: Creare modelli di elementi](../ide/how-to-create-item-templates.md).  
  
2.  Aggiungere gli attributi `TargetFileName` a ogni elemento `ProjectItem`. Impostare i valori degli attributi `TargetFileName` su $fileinputname$.*EstensioneFile*, dove *EstensioneFile* è l'estensione del file da inserire nel modello. Ad esempio:  
  
    ```  
    <ProjectItem TargetFileName="$fileinputname$.vb">  
        Form1.vb  
    </ProjectItem>  
    <ProjectItem TargetFileName="$fileinputname$.Designer.vb">  
        Form1.Designer.vb  
    </ProjectItem>  
    <ProjectItem TargetFileName="$fileinputname$.resx">  
        Form1.resx  
    </ProjectItem>  
    ```  
  
     Quando un elemento derivato da questo modello viene aggiunto a un progetto, i nomi dei file saranno basati sul nome immesso dall'utente nella finestra di dialogo **Aggiungi nuovo elemento**.  
  
3.  Selezionare i file da includere nel modello, fare clic con il pulsante destro del mouse sulla selezione, scegliere **Invia a** e quindi fare clic su **Cartella compressa**. I file selezionati verranno compressi in un file ZIP.  
  
4.  Inserire il file con estensione zip nel percorso del modello di elemento dell'utente. Per impostazione predefinita, la directory è \Documenti\Visual Studio *Versione*\Templates\ItemTemplates\\. Per altre informazioni, vedere [Procedura: Individuare e organizzare modelli](../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra un modello di Windows Forms di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Quando viene creato un elemento basato su questo modello, i nomi dei tre file creati corrisponderanno al nome immesso nella finestra di dialogo **Aggiungi nuovo elemento**.  
  
```  
<VSTemplate Version="2.0.0" Type="Item"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-file Item Template</Name>  
        <Icon>Icon.ico</Icon>  
        <Description>An example of a multi-file item template</Description>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem TargetFileName="$fileinputname$.vb" SubType="Form">  
            Form1.vb  
        </ProjectItem>  
        <ProjectItem TargetFileName="$fileinputname$.Designer.vb">  
            Form1.Designer.vb  
        </ProjectItem>  
        <ProjectItem TargetFileName="$fileinputname$.resx">  
            Form1.resx  
        </ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)   
 [Procedura: Creare modelli di elementi](../ide/how-to-create-item-templates.md)   
 [Parametri di modello](../ide/template-parameters.md)   
 [Procedura: Sostituire i parametri di un modello](../ide/how-to-substitute-parameters-in-a-template.md)