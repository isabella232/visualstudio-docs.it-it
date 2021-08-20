---
title: Aggiunta di un menu alla barra Visual Studio menu | Microsoft Docs
description: Informazioni su come aggiungere un menu alla barra dei menu del Visual Studio di sviluppo integrato (IDE).
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f622200066192304b2d066ad3bd3839ab2cbc0c9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122112009"
---
# <a name="add-a-menu-to-the-visual-studio-menu-bar"></a>Aggiungere un menu alla barra Visual Studio menu

Questa procedura dettagliata illustra come aggiungere un menu alla barra dei menu del Visual Studio di sviluppo integrato (IDE). La barra dei menu dell'IDE contiene categorie di menu, ad esempio **File**, **Modifica**, **Visualizza**, **Finestra** e **Guida**.

Prima di aggiungere un nuovo menu alla barra Visual Studio, valutare se i comandi devono essere inseriti all'interno di un menu esistente. Per altre informazioni sul posizionamento dei comandi, vedere [Menu e comandi per Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

I menu vengono dichiarati nel file *con estensione vsct* del progetto. Per altre informazioni sui menu e sui file con estensione *vsct,* vedere [Comandi, menu e barre degli strumenti.](../extensibility/internals/commands-menus-and-toolbars.md)

Completando questa procedura dettagliata, è possibile creare un menu denominato **Menu test** contenente un comando.

:::moniker range=">=vs-2019"
> [!NOTE]
> A partire Visual Studio 2019, i menu di primo livello contributo dalle estensioni vengono inseriti nel menu **Estensioni.**
:::moniker-end

## <a name="prerequisites"></a>Prerequisiti

A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-vsix-project-that-has-a-custom-command-item-template"></a>Creare un progetto VSIX con un modello di elemento di comando personalizzato

1. Creare un progetto VSIX denominato `TopLevelMenu` . È possibile trovare il modello di progetto VSIX nella finestra **di dialogo Project** nuovo progetto cercando "vsix".  Per altre informazioni, vedere [Creare un'estensione con un comando di menu.](../extensibility/creating-an-extension-with-a-menu-command.md)

::: moniker range="vs-2017"

2. All'apertura del progetto, aggiungere un modello di elemento di comando personalizzato denominato **TestCommand**. Nella finestra **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi**  >   **nuovo elemento.** Nella finestra **di dialogo Aggiungi nuovo** elemento passare a Visual **C# /Extensibility** e selezionare **Comando personalizzato.** Nel campo **Nome** nella parte inferiore della finestra modificare il nome del file di comando in *TestCommand.cs*.

::: moniker-end

::: moniker range=">=vs-2019"

2. All'apertura del progetto, aggiungere un modello di elemento di comando personalizzato denominato **TestCommand**. Nella finestra **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi**  >   **nuovo elemento.** Nella finestra **di dialogo Aggiungi nuovo** elemento passare a Visual **C# /Extensibility** e selezionare **Comando**. Nel campo **Nome** nella parte inferiore della finestra modificare il nome del file di comando in *TestCommand.cs*.

::: moniker-end

## <a name="create-a-menu-on-the-ide-menu-bar"></a>Creare un menu nella barra dei menu dell'IDE

::: moniker range="vs-2017"

1. In **Esplora soluzioni** aprire *TestCommandPackage.vsct.*

    Alla fine del file è presente un `<Symbols>` nodo che contiene diversi `<GuidSymbol>` nodi. Nel nodo denominato `guidTestCommandPackageCmdSet` aggiungere un nuovo simbolo, come indicato di seguito:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Creare un nodo `<Menus>` vuoto nel nodo , subito prima di `<Commands>` `<Groups>` . Nel `<Menus>` nodo aggiungere un `<Menu>` nodo come indicato di seguito:

   ```xml
   <Menus>
         <Menu guid="guidTestCommandPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>Test Menu</ButtonText>
           </Strings>
       </Menu>
   </Menus>
   ```

    I `guid` valori e del menu `id` specificano il set di comandi e il menu specifico nel set di comandi.

    I `guid` valori e dell'elemento padre posizionano il menu nella sezione della barra dei menu Visual Studio che contiene i menu Strumenti e `id` Componenti aggiuntivi.

    `<ButtonText>`L'elemento specifica che il testo deve essere visualizzato nella voce di menu.

3. Nella sezione trovare e modificare l'elemento in modo che `<Groups>` punti al menu appena `<Group>` `<Parent>` aggiunto:

   ```xml
   <Groups>
       <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
       </Group>
   </Groups>
   ```

    In questo modo il gruppo fa parte del nuovo menu.

::: moniker-end

::: moniker range=">=vs-2019"

1. In **Esplora soluzioni** aprire *TopLevelMenuPackage.vsct.*

    Alla fine del file è presente un `<Symbols>` nodo che contiene diversi `<GuidSymbol>` nodi. Nel nodo denominato `guidTopLevelMenuPackageCmdSet` aggiungere un nuovo simbolo, come indicato di seguito:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Creare un nodo `<Menus>` vuoto nel nodo , subito prima di `<Commands>` `<Groups>` . Nel `<Menus>` nodo aggiungere un `<Menu>` nodo come indicato di seguito:

   ```xml
   <Menus>
         <Menu guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>Test Menu</ButtonText>
           </Strings>
       </Menu>
   </Menus>
   ```

    I `guid` valori e del menu `id` specificano il set di comandi e il menu specifico nel set di comandi.

    I `guid` valori e dell'elemento padre posizionano il menu nella sezione della barra dei menu Visual Studio che contiene i menu Strumenti e `id` Componenti aggiuntivi.

    `<ButtonText>`L'elemento specifica che il testo deve essere visualizzato nella voce di menu.

3. Nella sezione trovare e modificare l'elemento in modo che `<Groups>` punti al menu appena `<Group>` `<Parent>` aggiunto:

   ```xml
   <Groups>
       <Group guid="guidTopLevelMenuPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu"/>
       </Group>
   </Groups>
   ```

    In questo modo il gruppo fa parte del nuovo menu.

::: moniker-end

4. Nella `<Buttons>` sezione trovare il `<Button>` nodo . Nel nodo modificare quindi `<Strings>` `<ButtonText>` l'elemento in `Test Command` .

    Si noti che [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] il modello Package ha generato un elemento il cui padre è impostato su `Button` `MyMenuGroup` . Di conseguenza, questo comando viene visualizzato nel menu.

## <a name="build-and-test-the-extension"></a>Compilare e testare l'estensione

1. Compilare il progetto e avviare il debug. Verrà visualizzata un'istanza dell'istanza sperimentale.

::: moniker range="vs-2017"

2. La barra dei menu nell'istanza sperimentale deve contenere un menu **test.**

::: moniker-end

::: moniker range=">=vs-2019"

2. Il menu **Estensioni** nell'istanza sperimentale deve contenere un menu **Test.**

::: moniker-end

3. Scegliere **Comando test** dal menu **Test**.

    Dovrebbe essere visualizzata una finestra di messaggio con il messaggio "TestCommand Inside TopLevelMenu.TestCommand.MenuItemCallback()".

## <a name="see-also"></a>Vedi anche

- [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)
