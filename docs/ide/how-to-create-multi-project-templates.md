---
title: Creare modelli per più progetti
ms.date: 04/17/2019
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-project
- project templates, multi-project
- multi-project templates
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 6da7464f5e22e186edff7671744c2605bee3c9ad
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591086"
---
# <a name="how-to-create-multi-project-templates"></a>Procedura: Creare modelli per più progetti

I modelli multiprogetto fungono da contenitori per due o più progetti. Quando si crea un progetto basato su un modello per più progetti, ogni progetto del modello viene aggiunto alla soluzione.

Un modello per più progetti contiene due o più modelli di progetto e un modello radice di tipo **ProjectGroup**.

I modelli per più progetti funzionano in modo diverso rispetto ai modelli per progetto singolo. Presentano le caratteristiche specifiche seguenti:

- Non è possibile assegnare nomi ai singoli progetti di un modello per più progetti se il modello viene usato per creare un nuovo progetto. Usare invece l'attributo **ProjectName** nell'elemento **ProjectTemplateLink** del file con estensione *vstemplate* per specificare il nome di ogni progetto.

- I modelli per più progetti possono contenere progetti per linguaggi diversi, ma l'intero modello può essere inserito in una sola categoria. Specificare la categoria del modello nell'elemento **ProjectType** del file con estensione *vstemplate*.

Un modello per più progetti deve includere gli elementi seguenti, compressi in un file con estensione *zip*:

- Un file radice con estensione *vstemplate* per l'intero modello per più progetti. Questo file radice con estensione *vstemplate* contiene metadati che vengono visualizzati nella finestra di dialogo in cui si crea un nuovo progetto. Specifica inoltre dove trovare i file con estensione *vstemplate* per i progetti nel modello. Questo file deve trovarsi nella radice del file con estensione *zip*.

- Due o più cartelle che contengono i file necessari per un modello di progetto completo. Le cartelle includono tutti i file di codice per il progetto e un file con estensione *vstemplate* per il progetto.

Ad esempio, il file con estensione *zip* di un modello per più progetti con due progetti può includere i file e le directory seguenti:

- *MultiProjectTemplate.vstemplate*
- *\Project1\MyTemplate.vstemplate*
- *\Project1\Project1.vbproj*
- *\Project1\Class.vb*
- *\Project2\MyTemplate.vstemplate*
- *\Project2\Project2.vbproj*
- *\Project2\Class.vb*

Il file radice con estensione *vstemplate* per un modello per più progetti differisce da un modello per progetto singolo nei modi seguenti:

- L'attributo **Tipo** dell'elemento**VSTemplate** ha il valore **ProjectGroup** anziché **Project**. Ad esempio:

    ```xml
    <VSTemplate Version="2.0.0" Type="ProjectGroup"
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    ```

- L'elemento **TemplateContent** contiene un elemento **ProjectCollection** che ha uno o più elementi **ProjectTemplateLink** che definiscono i percorsi dei file con estensione *vstemplate* dei progetti inclusi. Ad esempio:

    ```xml
    <TemplateContent>
        <ProjectCollection>
            <ProjectTemplateLink>
                Project1\MyTemplate.vstemplate
            </ProjectTemplateLink>
            <ProjectTemplateLink>
                Project2\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
    ```

> [!TIP]
> Se si vuole che solo il modello per più progetti venga visualizzato nella finestra di dialogo Nuovo progetto, anziché i singoli progetti che contiene, contrassegnare i modelli interni come [nascosti](../extensibility/hidden-element-visual-studio-templates.md). Ad esempio:
>
> ```xml
> <VSTemplate Type="Project" ... >
>     <TemplateData>
>         ...
>         <Hidden>true</Hidden>
>     </TemplateData>
>     ...
> </VSTemplate>
> ```

## <a name="create-a-multi-project-template-from-an-existing-solution"></a>Creare un modello per più progetti da una soluzione esistente

1. Creare una soluzione e aggiungere due o più progetti.

2. Personalizzare i progetti fino a quando non sono pronti per essere esportati in un modello.

   > [!TIP]
   > Se si usano [parametri di modello](template-parameters.md) e si vuole fare riferimento alle variabili del modello padre, aggiungere il prefisso `ext_` al nome del parametro. Ad esempio `$ext_safeprojectname$`. Impostare inoltre l'attributo **CopyParameters** dell'elemento **ProjectTemplateLink** su **true**.
   >
   > ```xml
   > <ProjectTemplateLink ProjectName="MyProject" CopyParameters="true">...</ProjectTemplateLink>
   > ```

3. Nel menu **Progetto** scegliere**Esporta modello**.

   Viene aperta l'**Esportazione guidata modelli**.

4. Nella pagina **Scegliere il tipo di modello** selezionare **Modello di progetto**. Selezionare uno dei progetti che si vuole esportare in un modello e quindi scegliere **Avanti**. È possibile ripetere questi passaggi per ogni progetto della soluzione.

5. Nella pagina **Selezionare le opzioni del modello** immettere il nome e una descrizione, un'icona e un'immagine di anteprima facoltative per il modello. Scegliere **Fine**.

   Il progetto viene esportato in un file con estensione *zip* e inserito nel percorso di output specificato.

   > [!NOTE]
   > Ogni progetto deve essere esportato in un modello separatamente, quindi ripetere i passaggi precedenti per ogni progetto nella soluzione.

6. Creare una directory per il modello con una sottodirectory per ogni progetto.

7. Estrarre il contenuto del file con estensione *zip* di ogni progetto nella sottodirectory corrispondente appena creata.

8. Nella directory di base creare un file XML con estensione *vstemplate*. Questo file contiene i metadati del modello per più progetti. Vedere l'esempio che segue per la struttura del file. Assicurarsi di specificare il percorso relativo di ogni file con estensione *vstemplate*.

9. Selezionare tutti i file nella directory base, quindi facendo clic con il pulsante destro del mouse o dal menu di scelta rapida scegliere **Invia a** > **Cartella compressa**.

   I file e le cartelle vengono compressi in un file con estensione *zip*.

10. Copiare il file con estensione *zip* nella directory del modello di progetto utente. Per impostazione predefinita la directory è *%USERPROFILE%\Documents\Visual Studio \<versione\>\Templates\ProjectTemplates*.

11. In Visual Studio scegliere **File** > **Nuovo** > **Progetto** e verificare che sia visualizzato il modello.

## <a name="two-project-example"></a>Esempio con due progetti

Questo esempio illustra un file radice semplice con estensione *vstemplate* per più progetti. In questo esempio il modello contiene due progetti, **My Windows Application** e **My Class Library**. L'attributo **ProjectName** dell'elemento **ProjectTemplateLink** specifica il nome assegnato al progetto.

> [!TIP]
> Se l'attributo **ProjectName** non è specificato, viene usato come nome del progetto il nome del file con estensione *vstemplate*.

```xml
<VSTemplate Version="2.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <ProjectTemplateLink ProjectName="My Windows Application">
                WindowsApp\MyTemplate.vstemplate
            </ProjectTemplateLink>
            <ProjectTemplateLink ProjectName="My Class Library">
                ClassLib\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="example-with-solution-folders"></a>Esempio con cartelle della soluzione

Questo esempio usa l'elemento **SolutionFolder** per suddividere i progetti in due gruppi, **Math Classes** e **Graphics Classes**. Il modello contiene quattro progetti, due dei quali vengono inseriti in ogni cartella della soluzione.

```xml
<VSTemplate Version="2.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <SolutionFolder Name="Math Classes">
                <ProjectTemplateLink ProjectName="MathClassLib1">
                    MathClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="MathClassLib2">
                    MathClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
            <SolutionFolder Name="Graphics Classes">
                <ProjectTemplateLink ProjectName="GraphicsClassLib1">
                    GraphicsClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="GraphicsClassLib2">
                    GraphicsClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Vedere anche

- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)
- [Procedura: Creare modelli di progetto](../ide/how-to-create-project-templates.md)
- [Riferimento allo schema di modello di Visual Studio (estendibilità)](../extensibility/visual-studio-template-schema-reference.md)
- [Elemento SolutionFolder (modelli di Visual Studio)](../extensibility/solutionfolder-element-visual-studio-templates.md)
- [Elemento ProjectTemplateLink (modelli di Visual Studio)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)
