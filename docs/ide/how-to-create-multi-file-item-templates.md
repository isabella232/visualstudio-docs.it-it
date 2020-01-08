---
title: Creazione di modelli di elemento a più file
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: e8a6e5358a87e3d64b341c89b8ffd4cd3cf3e325
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593733"
---
# <a name="how-to-create-multi-file-item-templates"></a>Procedura: Creare modelli di elementi a più file

Sebbene i modelli di elementi possano specificare un solo elemento, in alcuni casi l'elemento è costituito da più file. Ad esempio, un modello di elemento di Windows Forms richiede i tre file seguenti:

- Un file che contiene il codice per il modulo

- Un file che contiene le informazioni della finestra di progettazione per il modulo

- Un file che contiene le risorse incorporate per il modulo

Per i modelli di elementi a più file è necessario specificare i parametri per assicurarsi che vengano usate le estensioni di file corrette quando si crea l'elemento. Se si crea un modello di elemento a più file usando l'**Esportazione guidata modelli**, questi parametri vengono generati automaticamente e non è richiesta alcuna ulteriore modifica.

## <a name="use-the-export-template-wizard"></a>Usare l'Esportazione guidata modelli

È possibile creare un modello di elemento a più file con la stessa procedura usata per un modello di elemento a file singolo. Vedere [Procedura: Creare modelli di elementi](../ide/how-to-create-item-templates.md). Nella pagina **Selezionare l'elemento da esportare** della procedura guidata selezionare il file con file dipendenti, ad esempio un file modulo di Windows Form. La procedura guidata include automaticamente tutti i file dipendenti, ad esempio i file della finestra di progettazione e di risorse, nel modello.

## <a name="manually-create-a-multi-file-item-template"></a>Creare manualmente un modello di elemento a più file

1. Creare il modello di elemento come se si creasse manualmente un modello di elemento a file singolo, ma includere ogni file che costituisce l'elemento a più file.

1. Nel file XML con estensione *vstemplate*, aggiungere un elemento `ProjectItem` per ogni singolo file, quindi aggiungere un attributo `TargetFileName` a questo elemento. Impostare il valore dell'attributo `TargetFileName` su $fileinputname$.*EstensioneFile*, dove *EstensioneFile* è l'estensione del file da inserire nel modello. Ad esempio:

    ```xml
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

     > [!NOTE]
     > Quando un elemento derivato da questo modello viene aggiunto a un progetto, i nomi dei file deriveranno dal nome immesso dall'utente nella finestra di dialogo **Aggiungi nuovo elemento**.

1. Selezionare i file da includere nel modello, fare clic con il pulsante destro del mouse sulla selezione e scegliere **Invia a** > **Cartella compressa**.

   I file selezionati verranno compressi in un file con estensione *zip*.

1. Copiare il file *.zip* nel percorso del modello di elemento dell'utente. Per impostazione predefinita, la directory è *%USERPROFILE%\Documenti\Visual Studio \<Versione\>\Templates\ItemTemplates*. Per altre informazioni, vedere [Procedura: Individuare e organizzare modelli](../ide/how-to-locate-and-organize-project-and-item-templates.md).

1. Chiudere e riaprire Visual Studio.

1. Creare un nuovo progetto o aprire un progetto esistente, quindi scegliere **Progetto** > **Aggiungi nuovo elemento** o premere **CTRL**+**MAIUSC**+**A**.

   Il modello di elemento a più file appare nella finestra di dialogo **Aggiungi nuovo elemento**.

## <a name="example"></a>Esempio

L'esempio seguente illustra un modello di Windows Form. Quando viene creato un elemento basato su questo modello, i nomi dei tre file creati corrisponderanno al nome immesso nella finestra di dialogo **Aggiungi nuovo elemento**.

```xml
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

- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
- [Procedura: Creare modelli di elementi](../ide/how-to-create-item-templates.md)
- [Parametri di modello](../ide/template-parameters.md)
- [Procedura: Sostituire i parametri di un modello](../ide/how-to-substitute-parameters-in-a-template.md)
