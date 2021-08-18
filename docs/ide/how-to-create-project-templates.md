---
title: Creare modelli di progetto
description: Informazioni su come usare l'Esportazione guidata modelli e altri metodi per creare modelli di progetto in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- project templates [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.openlocfilehash: e1e4a31f0e82c262527da80fc85246de7d7c6c1a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086131"
---
# <a name="how-to-create-project-templates"></a>Procedura: Creare modelli di progetto

Questo argomento spiega come creare un modello usando l'**Esportazione guidata modelli**, che consente di creare un pacchetto del modello in un file con estensione *zip*.

## <a name="use-the-export-template-wizard"></a>Usare l'Esportazione guidata modelli

1. Creare un progetto.

    > [!NOTE]
    > Quando si assegna il nome a un progetto che fungerà da origine per un modello, usare solo caratteri di identificatore validi. In caso contrario, possono verificarsi errori di compilazione nei progetti creati dal modello. Per altre informazioni sui caratteri di identificatore valido, vedere [Nomi di elementi dichiarati (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names) o [Identificatori (C++)](/cpp/cpp/identifiers-cpp). In alternativa, è possibile usare [parametri di modello](../ide/template-parameters.md) per specificare nomi "sicuri" per le classi e gli spazi dei nomi.

2. Modificare il progetto finché non è pronto per l'esportazione come modello. Ad esempio, può essere necessario modificare i file del codice per indicare dove deve essere applicata la sostituzione dei parametri. Vedere [Procedura: Sostituire i parametri di un modello](../ide/how-to-substitute-parameters-in-a-template.md).

3. Nel menu **Project** scegliere **Esporta modello**.

   Verrà **visualizzata l'Esportazione guidata** modello.

4. Nella pagina **Scegliere il tipo di modello** selezionare **Modello di progetto**. Selezionare il progetto che si vuole esportare in un modello e quindi scegliere **Avanti**.

::: moniker range="vs-2017"

5. Nella pagina **Selezione opzioni modello** immettere un nome e una descrizione facoltativa, un'icona e un'immagine di anteprima per il modello. Questi elementi verranno visualizzati nella finestra di dialogo **Nuovo progetto**. Scegliere **Fine**.

   Il progetto viene esportato in un file con estensione *zip*, inserito nel percorso di output specificato e, se questa azione è stata selezionata, importato in Visual Studio.

Per trovare il modello nella finestra di dialogo **Nuovo progetto**, espandere **Installato** e quindi espandere la categoria che corrisponde all'elemento `ProjectType` nel file con estensione *vstemplate*. Ad esempio, un file con estensione *vstemplate* che contiene `<ProjectType>CSharp</ProjectType>` appare in **Installato** > **Visual C#** per impostazione predefinita. È possibile organizzare il modello in una sottodirectory del tipo di progetto semplicemente creando una cartella in quella directory e inserendo il file con estensione *zip* del modello nella cartella. Per altre informazioni, vedere [Procedura: Individuare e organizzare i modelli.](../ide/how-to-locate-and-organize-project-and-item-templates.md)

::: moniker-end

::: moniker range=">=vs-2019"

5. Nella pagina **Selezione opzioni modello** immettere un nome e una descrizione facoltativa, un'icona e un'immagine di anteprima per il modello. Questi elementi verranno visualizzati nella finestra di dialogo in cui si crea un nuovo progetto. Scegliere **Fine**.

   Il progetto viene esportato in un file con estensione *zip*, inserito nel percorso di output specificato e, se questa azione è stata selezionata, importato in Visual Studio.

Per trovare il modello nella finestra di dialogo in cui si crea un nuovo progetto, cercarlo per nome o scorrere l'elenco. Filtrare i modelli utente in base al linguaggio o al tipo di progetto al momento non è possibile.

::: moniker-end

## <a name="other-ways-to-create-project-templates"></a>Altri modi per creare modelli di progetti

È possibile creare manualmente modelli di progetti raccogliendo i file che costituiscono il progetto in una cartella e creando un file XML con estensione *vstemplate* con i metadati appropriati. Per altre informazioni, vedere [Procedura: Creare manualmente modelli Web](../ide/how-to-manually-create-web-templates.md).

Se Visual Studio SDK è installato, è possibile eseguire il wrapping del modello finito in un file VSIX per la distribuzione con il modello **Progetto VSIX**. Per altre informazioni, vedere [Introduzione al modello di progetto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).

## <a name="see-also"></a>Vedi anche

- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
- [Procedura: Creare modelli di elemento](../ide/how-to-create-item-templates.md)
- [Introduzione al modello di progetto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)
- [Personalizzare modelli di progetto e modelli di elemento](customizing-project-and-item-templates.md)
