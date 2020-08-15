---
title: Aggiunta di un menu alla barra dei menu di Visual Studio | Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa3ab53bbda2582d1a9b3c60ac07fd3617d51ddf
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/15/2020
ms.locfileid: "88248779"
---
# <a name="add-a-menu-to-the-visual-studio-menu-bar"></a>Aggiungere un menu alla barra dei menu di Visual Studio

Questa procedura dettagliata illustra come aggiungere un menu alla barra dei menu di Visual Studio Integrated Development Environment (IDE). La barra dei menu dell'IDE contiene le categorie di menu, ad esempio **file**, **modifica**, **Visualizza**, **finestra**e **Guida**.

Prima di aggiungere un nuovo menu alla barra dei menu di Visual Studio, valutare se i comandi devono essere posizionati all'interno di un menu esistente. Per ulteriori informazioni sulla selezione host dei comandi, vedere [menu e comandi per Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

I menu vengono dichiarati nel file con *estensione vsct* del progetto. Per ulteriori informazioni sui menu e sui file con *estensione vsct* , vedere [comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md).

Completando questa procedura dettagliata, è possibile creare un menu denominato **test** che contiene un solo comando.

:::moniker range=">=vs-2019"
> [!NOTE]
> A partire da Visual Studio 2019, i menu di primo livello forniti dalle estensioni vengono inseriti nel menu **estensioni** .
:::moniker-end

## <a name="prerequisites"></a>Prerequisiti

A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vsix-project-that-has-a-custom-command-item-template"></a>Creare un progetto VSIX con un modello di elemento di comando personalizzato

1. Creare un progetto VSIX denominato `TopLevelMenu` . È possibile trovare il modello di progetto VSIX nella finestra di dialogo **nuovo progetto** cercando "VSIX".  Per altre informazioni, vedere [creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).

::: moniker range="vs-2017"

2. Quando si apre il progetto, aggiungere un modello di elemento di comando personalizzato denominato **TestCommand**. Nella **Esplora soluzioni**selezionare e mantenere (oppure fare clic con il pulsante destro del mouse) sul nodo del progetto e selezionare **Aggiungi**  >   **nuovo elemento**. Nella finestra di dialogo **Aggiungi nuovo elemento** passare a **Visual C#/extensibility** e selezionare **comando personalizzato**. Nel campo **nome** nella parte inferiore della finestra modificare il nome del file di comando in *TestCommand.cs*.

::: moniker-end

::: moniker range=">=vs-2019"

2. Quando si apre il progetto, aggiungere un modello di elemento di comando personalizzato denominato **TestCommand**. Nella **Esplora soluzioni**selezionare e mantenere (oppure fare clic con il pulsante destro del mouse) sul nodo del progetto e selezionare **Aggiungi**  >   **nuovo elemento**. Nella finestra di dialogo **Aggiungi nuovo elemento** passare a **Visual C#/extensibility** e selezionare **comando**. Nel campo **nome** nella parte inferiore della finestra modificare il nome del file di comando in *TestCommand.cs*.

::: moniker-end

## <a name="create-a-menu-on-the-ide-menu-bar"></a>Creare un menu nella barra dei menu dell'IDE

::: moniker range="vs-2017"

1. In **Esplora soluzioni**aprire *TestCommandPackage. vsct*.

    Alla fine del file è presente un `<Symbols>` nodo che contiene diversi `<GuidSymbol>` nodi. Nel nodo denominato `guidTestCommandPackageCmdSet` aggiungere un nuovo simbolo, come indicato di seguito:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Creare un `<Menus>` nodo vuoto nel `<Commands>` nodo, immediatamente prima `<Groups>` . Nel `<Menus>` nodo aggiungere un `<Menu>` nodo, come indicato di seguito:

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

    I `guid` `id` valori e del menu specificano il set di comandi e il menu specifico nel set di comandi.

    I `guid` `id` valori e dell'elemento padre posizionano il menu nella sezione della barra dei menu di Visual Studio contenente i menu strumenti e componenti aggiuntivi.

    L' `<ButtonText>` elemento specifica che il testo deve essere visualizzato nella voce di menu.

3. Nella `<Groups>` sezione trovare `<Group>` e modificare l' `<Parent>` elemento in modo che punti al menu appena aggiunto:

   ```xml
   <Groups>
       <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
       </Group>
   </Groups>
   ```

    In questo modo la parte del gruppo del nuovo menu.

::: moniker-end

::: moniker range=">=vs-2019"

1. In **Esplora soluzioni**aprire *TopLevelMenuPackage. vsct*.

    Alla fine del file è presente un `<Symbols>` nodo che contiene diversi `<GuidSymbol>` nodi. Nel nodo denominato `guidTopLevelMenuPackageCmdSet` aggiungere un nuovo simbolo, come indicato di seguito:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Creare un `<Menus>` nodo vuoto nel `<Commands>` nodo, immediatamente prima `<Groups>` . Nel `<Menus>` nodo aggiungere un `<Menu>` nodo, come indicato di seguito:

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

    I `guid` `id` valori e del menu specificano il set di comandi e il menu specifico nel set di comandi.

    I `guid` `id` valori e dell'elemento padre posizionano il menu nella sezione della barra dei menu di Visual Studio contenente i menu strumenti e componenti aggiuntivi.

    L' `<ButtonText>` elemento specifica che il testo deve essere visualizzato nella voce di menu.

3. Nella `<Groups>` sezione trovare `<Group>` e modificare l' `<Parent>` elemento in modo che punti al menu appena aggiunto:

   ```xml
   <Groups>
       <Group guid="guidTopLevelMenuPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu"/>
       </Group>
   </Groups>
   ```

    In questo modo la parte del gruppo del nuovo menu.

::: moniker-end

4. Nella `<Buttons>` sezione trovare il `<Button>` nodo. Quindi, nel `<Strings>` nodo, modificare l' `<ButtonText>` elemento in `Test Command` .

    Si noti che il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modello di pacchetto ha generato un `Button` elemento il cui padre è impostato su `MyMenuGroup` . Questo comando viene quindi visualizzato nel menu.

## <a name="build-and-test-the-extension"></a>Compilare e testare l'estensione

1. Compilare il progetto e avviare il debug. Verrà visualizzata un'istanza dell'istanza sperimentale.

::: moniker range="vs-2017"

2. La barra dei menu nell'istanza sperimentale deve contenere un menu di **menu test** .

::: moniker-end

::: moniker range=">=vs-2019"

2. Il menu **estensioni** nell'istanza sperimentale deve contenere un menu di **menu test** .

::: moniker-end

3. Scegliere **Test Command**dal menu **test** .

    Verrà visualizzata una finestra di messaggio con il messaggio "TestCommand all'interno di TopLevelMenu. TestCommand. MenuItemCallback ()".

## <a name="see-also"></a>Vedere anche

- [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)
