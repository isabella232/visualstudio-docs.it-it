---
title: Aggiunta di un menu alla barra dei menu di Visual Studio . Documenti Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91e5a6e1714dbb87abc67fbf722c3bbd1a194a5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740306"
---
# <a name="add-a-menu-to-the-visual-studio-menu-bar"></a>Aggiungere un menu alla barra dei menu di Visual StudioAdd a menu to the Visual Studio menu bar

Questa procedura dettagliata viene illustrato come aggiungere un menu alla barra dei menu dell'ambiente di sviluppo integrato (IDE) di Visual Studio. La barra dei menu dell'IDE contiene categorie di menu quali **File**, **Modifica**, **Visualizza**, **Finestra**e **Guida**.

Prima di aggiungere un nuovo menu alla barra dei menu di Visual Studio, valutare se i comandi devono essere inseriti all'interno di un menu esistente. Per ulteriori informazioni sul posizionamento dei comandi, vedere [Menu e comandi per Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

I menu vengono dichiarati nel file *vsct* del progetto. Per ulteriori informazioni sui menu e sui file *vsct,* consultate [Comandi, menu e barre degli strumenti.](../extensibility/internals/commands-menus-and-toolbars.md)

Completando questa procedura dettagliata, è possibile creare un menu denominato **TestMenu** che contiene un comando.

> [!NOTE]
> In VS 2019, i menu di primo livello forniti dalle estensioni vengono posizionati nel menu **Estensioni.**

## <a name="prerequisites"></a>Prerequisiti

A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It is included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-vsix-project-that-has-a-custom-command-item-template"></a>Creare un progetto VSIX con un modello di elemento di comando personalizzatoCreate a VSIX project that has a custom command item template

1. Creare un progetto `TopLevelMenu`VSIX denominato . È possibile trovare il modello di progetto VSIX nella finestra di dialogo **Nuovo progetto** cercando "vsix".  Per ulteriori informazioni, consultate [Creare un'estensione con un comando](../extensibility/creating-an-extension-with-a-menu-command.md)di menu.

2. Quando si apre il progetto, aggiungere un modello di elemento di comando personalizzato denominato **TestCommand**. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi** >  **nuovo elemento**. Nella finestra di dialogo **Aggiungi nuovo elemento** passare a **Custom Command** **Visual C.** Nel campo **Nome** nella parte inferiore della finestra modificare il nome del file di comando *in TestCommand.cs*.

## <a name="create-a-menu-on-the-ide-menu-bar"></a>Creare un menu sulla barra dei menu dell'IDE

::: moniker range="vs-2017"

1. In **Esplora soluzioni**aprire *TestCommandPackage.vsct*.

    Alla fine del file, è \<presente un nodo \<Symbols> che contiene diversi nodi GuidSymbol>. Nel nodo denominato guidTestCommandPackageCmdSet aggiungere un nuovo simbolo, come indicato di seguito:In the node named guidTestCommandPackageCmdSet, add a new symbol, as follows:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Creare un \<nodo Menus \<> vuoto nel \<nodo Comandi>, appena prima della> dei gruppi. Nel \<menu> nodo, \<aggiungere un menu> nodo, come indicato di seguito:In the Menus> node, add a Menu> node, as follows:

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

    I `guid` `id` valori e del menu specificano il set di comandi e il menu specifico nel set di comandi.

    I `guid` `id` valori e dell'elemento padre posizionano il menu nella sezione della barra dei menu di Visual Studio che contiene i menu Strumenti e componenti aggiuntivi.

    Il valore `CommandName` della stringa specifica che il testo deve essere visualizzato nella voce di menu.

3. Nella \<sezione> Gruppi, \<trova il \<> Gruppo e modifica l'elemento> padre in modo che punti al menu appena aggiunto:

   ```csharp
   <Groups>
         <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    In questo modo il gruppo fa parte del nuovo menu.

::: moniker-end

::: moniker range=">=vs-2019"

1. In **Esplora soluzioni**aprire *TopLevelMenuPackage.vsct*.

    Alla fine del file, è \<presente un nodo \<Symbols> che contiene diversi nodi GuidSymbol>. Nel nodo denominato guidTopLevelMenuPackageCmdSet, aggiungere un nuovo simbolo, come indicato di seguito:In the node named guidTopLevelMenuPackageCmdSet, add a new symbol, as follows:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Creare un \<nodo Menus \<> vuoto nel \<nodo Comandi>, appena prima della> dei gruppi. Nel \<menu> nodo, \<aggiungere un menu> nodo, come indicato di seguito:In the Menus> node, add a Menu> node, as follows:

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

    I `guid` `id` valori e del menu specificano il set di comandi e il menu specifico nel set di comandi.

    I `guid` `id` valori e dell'elemento padre posizionano il menu nella sezione della barra dei menu di Visual Studio che contiene i menu Strumenti e componenti aggiuntivi.

    Il valore `CommandName` della stringa specifica che il testo deve essere visualizzato nella voce di menu.

3. Nella \<sezione> Gruppi, \<trova il \<> Gruppo e modifica l'elemento> padre in modo che punti al menu appena aggiunto:

   ```csharp
   <Groups>
         <Group guid="guidTopLevelMenuPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    In questo modo il gruppo fa parte del nuovo menu.

::: moniker-end

4. Trovare la sezione `Buttons`. Si noti che [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] il `Button` modello Package ha `MyMenuGroup`generato un elemento il cui elemento padre è impostato su . Di conseguenza, questo comando viene visualizzato nel menu.

## <a name="build-and-test-the-extension"></a>Compilare e testare l'estensione

1. Compilare il progetto e avviare il debug. Dovrebbe essere visualizzata un'istanza dell'istanza sperimentale.

::: moniker range="vs-2017"

2. La barra dei menu nell'istanza sperimentale deve contenere un menu **TestMenu.The** menu bar in the experimental instance should contain a TestMenu menu.

::: moniker-end

::: moniker range=">=vs-2019"

2. Il menu **Estensioni** nell'istanza sperimentale deve contenere un menu **TestMenu.The** Extensions menu in the experimental instance should contain a TestMenu menu.

::: moniker-end

3. Scegliere **Richiama comando**di prova dal menu **TestMenu** .

     Verrà visualizzata una finestra di messaggio con il messaggio "TestCommand Package Inside TopLevelMenu.TestCommand.MenuItemCallback()".

## <a name="see-also"></a>Vedere anche

- [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)
