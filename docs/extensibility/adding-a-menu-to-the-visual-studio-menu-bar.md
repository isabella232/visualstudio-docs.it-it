---
title: Aggiunta di un Menu alla barra dei Menu di Visual Studio | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c7ce5ab06eb641e94d6f972b888882ac1e53e2ee
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58195047"
---
# <a name="add-a-menu-to-the-visual-studio-menu-bar"></a>Aggiungere un menu alla barra dei menu di Visual Studio

Questa procedura dettagliata illustra come aggiungere un menu alla barra dei menu dell'ambiente di sviluppo integrato (IDE) di Visual Studio. Barra dei menu IDE contiene ad esempio le categorie di menu **File**, **Edit**, **visualizzazione**, **finestra**, e **Guida** .

Prima di aggiungere un nuovo menu alla barra dei menu di Visual Studio, è consigliabile se i comandi devono essere posizionati all'interno di un menu esistente. Per altre informazioni sul posizionamento dei comandi, vedere [menu e comandi per Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

I menu vengono dichiarati nel *vsct* file del progetto. Per altre informazioni sui menu e *vsct* i file, vedere [comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md).

Completando questa procedura dettagliata, è possibile creare un menu di scelta denominata **TestMenu** che contiene un unico comando.

> [!NOTE]
> In Visual Studio 2019, menu principali forniti dalle estensioni vengono posizionati sotto la **estensioni** menu.

## <a name="prerequisites"></a>Prerequisiti

A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vsix-project-that-has-a-custom-command-item-template"></a>Creare un progetto VSIX con un modello di elemento di comando personalizzato

1. Creare un progetto VSIX denominato `TopLevelMenu`. È possibile trovare il modello di progetto VSIX nel **nuovo progetto** dialogo eseguendo una ricerca per "vsix".  Per altre informazioni, vedere [creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Quando si apre il progetto, aggiungere un modello di elemento di comando personalizzato denominato **TestCommand**. Nel **Esplora soluzioni**, fare doppio clic sul nodo del progetto e selezionare **Add** >  **nuovo elemento**. Nel **Aggiungi nuovo elemento** finestra di dialogo passa alla **Visual C# / Extensibility** e selezionare **comando personalizzato**. Nel **Name** campo nella parte inferiore della finestra, modificare il nome di file di comando da *TestCommand.cs*.

## <a name="create-a-menu-on-the-ide-menu-bar"></a>Creare un menu nella barra dei menu dell'IDE

::: moniker range="vs-2017"

1. Nelle **Esplora soluzioni**aprire *TestCommandPackage.vsct*.

    Alla fine del file, è un \<simboli > nodo che contiene numerosi \<GuidSymbol > i nodi. Nel nodo denominato guidTestCommandPackageCmdSet, aggiungere un nuovo simbolo, come indicato di seguito:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Creare un oggetto vuoto \<menu > nodo il \<comandi > nodo, subito prima \<gruppi >. Nel \<menu > nodo, aggiungere un \<Menu > nodo, come indicato di seguito:

   ```xml
   <Menus>
         <Menu guid="guidTestCommandPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>TestMenu</ButtonText>
             <CommandName>TestMenu</CommandName>
           </Strings>
       </Menu>
   </Menus>
   ```

    Il `guid` e `id` valori del menu di specificano il set di comandi e menu specifico nel set di comandi.

    Il `guid` e `id` valori dell'elemento padre posizionare il menu di scelta nella sezione della barra dei menu di Visual Studio che contiene i menu degli strumenti e componenti aggiuntivi.

    Il valore della `CommandName` stringa specifica che il testo deve essere visualizzato nella voce di menu.

3. Nel \<gruppi > sezione, individuare il \<gruppo > e modificare il \<padre > elemento in modo che punti al menu appena aggiunto:

   ```csharp
   <Groups>
         <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    In questo modo la parte del gruppo del nuovo menu.

::: moniker-end

::: moniker range=">=vs-2019"

1. Nelle **Esplora soluzioni**aprire *TopLevelMenuPackage.vsct*.

    Alla fine del file, è un \<simboli > nodo che contiene numerosi \<GuidSymbol > i nodi. Nel nodo denominato guidTopLevelMenuPackageCmdSet, aggiungere un nuovo simbolo, come indicato di seguito:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Creare un oggetto vuoto \<menu > nodo il \<comandi > nodo, subito prima \<gruppi >. Nel \<menu > nodo, aggiungere un \<Menu > nodo, come indicato di seguito:

   ```xml
   <Menus>
         <Menu guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>TestMenu</ButtonText>
             <CommandName>TestMenu</CommandName>
           </Strings>
       </Menu>
   </Menus>
   ```

    Il `guid` e `id` valori del menu di specificano il set di comandi e menu specifico nel set di comandi.

    Il `guid` e `id` valori dell'elemento padre posizionare il menu di scelta nella sezione della barra dei menu di Visual Studio che contiene i menu degli strumenti e componenti aggiuntivi.

    Il valore della `CommandName` stringa specifica che il testo deve essere visualizzato nella voce di menu.

3. Nel \<gruppi > sezione, individuare il \<gruppo > e modificare il \<padre > elemento in modo che punti al menu appena aggiunto:

   ```csharp
   <Groups>
         <Group guid="guidTopLevelMenuPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    In questo modo la parte del gruppo del nuovo menu.

::: moniker-end

4. Trovare il `Buttons` sezione. Si noti che il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modello di pacchetto ha generato una `Button` elemento con il relativo elemento padre impostata su `MyMenuGroup`. Di conseguenza, questo comando viene visualizzata nel menu.

## <a name="build-and-test-the-extension"></a>Compilare e testare l'estensione

1. Compilare il progetto e avviare il debug. Un'istanza dell'istanza sperimentale dovrebbe essere visualizzato.

::: moniker range="vs-2017"

2. Barra dei menu nell'istanza sperimentale dovrebbe contenere una **TestMenu** menu.

::: moniker-end

::: moniker range=">=vs-2019"

2. Il **Extensions** menu nell'istanza sperimentale dovrebbe contenere un **TestMenu** menu.

::: moniker-end

3. Nel **TestMenu** menu, fare clic su **richiamare comandi Test**.

     Una finestra di messaggio dovrà essere visualizzato e visualizzare il messaggio "TestCommand pacchetto all'interno di TopLevelMenu.TestCommand.MenuItemCallback()".

## <a name="see-also"></a>Vedere anche

- [I comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)