---
title: 'Procedura: Creare modelli di elementi a più file | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
ms.assetid: fe3c4257-e383-4c80-b8af-c5c521959c33
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c6c6dde1880881bfb236909fde6ce6deb6bf596f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201849"
---
# <a name="how-to-create-multi-file-item-templates"></a>Procedura: Creare modelli di elementi a più file
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sebbene i modelli di elementi possano specificare un solo elemento, in alcuni casi l'elemento è costituito da più file. Ad esempio, un modello di elemento di Windows Forms per Visual Basic richiede i tre file seguenti:  
  
- Un file con estensione vb che contiene il codice per il modulo.  
  
- Un file designer.vb che contiene le informazioni della finestra di progettazione del modulo.  
  
- Un file con estensione resx che contiene le risorse incorporate del modulo.  
  
  Per i modelli di elementi a più file è necessario specificare i parametri per assicurarsi che vengano usate le estensioni dei nomi di file corrette quando l'elemento viene creato in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Se si crea un modello di elemento usando l'**Esportazione guidata modelli**, questi parametri vengono generati automaticamente e non è richiesta alcuna ulteriore modifica. La procedura seguente descrive come usare i parametri per assicurarsi che vengano create le estensioni dei nomi di file corrette.  
  
### <a name="to-manually-create-a-multi-file-item-template"></a>Per creare manualmente un modello di elemento a più file  
  
1. Creare il modello di elemento allo stesso modo in cui si crea un modello di elemento a file singolo. Per altre informazioni, vedere [Procedura: Creare modelli di elementi](../ide/how-to-create-item-templates.md).  
  
2. Aggiungere gli attributi `TargetFileName` a ogni elemento `ProjectItem`. Impostare i valori degli attributi `TargetFileName` su $fileinputname$.*EstensioneFile*, dove *EstensioneFile* è l'estensione del file da inserire nel modello. Ad esempio:  
  
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
  
3. Selezionare i file da includere nel modello, fare clic con il pulsante destro del mouse sulla selezione, scegliere **Invia a** e quindi fare clic su **Cartella compressa**. I file selezionati verranno compressi in un file ZIP.  
  
4. Inserire il file con estensione zip nel percorso del modello di elemento dell'utente. Per impostazione predefinita, la directory è \Documenti\Visual Studio *Versione*\Templates\ItemTemplates\\. Per altre informazioni, vedere [Procedura: Individuare e organizzare modelli](../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra un modello di Windows Forms di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Quando viene creato un elemento basato su questo modello, i nomi dei tre file creati corrisponderanno al nome immesso nella finestra di dialogo **Aggiungi nuovo elemento**.  
  
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
