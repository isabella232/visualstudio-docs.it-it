---
title: Aggiunta di un Menu alla barra dei Menu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
caps.latest.revision: 52
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 64ab627d785e8b00b5159969a01dc1102df30359
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184936"
---
# <a name="adding-a-menu-to-the-visual-studio-menu-bar"></a>Aggiunta di un menu alla barra dei menu di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa procedura dettagliata illustra come aggiungere un menu alla barra dei menu dell'ambiente di sviluppo integrato (IDE) di Visual Studio. Barra dei menu IDE contiene ad esempio le categorie di menu **File**, **Edit**, **visualizzazione**, **finestra**, e **Guida** .

 Prima di aggiungere un nuovo menu alla barra dei menu di Visual Studio, è consigliabile se i comandi devono essere posizionati all'interno di un menu esistente. Per altre informazioni sul posizionamento dei comandi, vedere [menu e comandi per Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

 I menu vengono dichiarati nel file con estensione vsct del progetto. Per altre informazioni sui menu e i file con estensione vsct, vedere [comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md).

 Completando questa procedura dettagliata, è possibile creare un menu di scelta denominata **TestMenu** che contiene un unico comando.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="creating-a-vsix-project-that-has-a-custom-command-item-template"></a>Creazione di un progetto VSIX con un modello di elemento di comando personalizzato

1. Creare un progetto VSIX denominato `TopLevelMenu`. È possibile trovare il modello di progetto VSIX nel **nuovo progetto** nella finestra di dialogo **Visual c#**  / **estendibilità**.  Per altre informazioni, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Quando si apre il progetto, aggiungere un modello di elemento di comando personalizzato denominato **TestCommand**. Nel **Esplora soluzioni**, fare doppio clic sul nodo del progetto e selezionare **Aggiungi / nuovo elemento**. Nel **Aggiungi nuovo elemento** finestra di dialogo passa alla **Visual c# / Extensibility** e selezionare **comando personalizzato**. Nel **Name** campo nella parte inferiore della finestra, modificare il nome di file di comando da **TestCommand.cs**.

## <a name="creating-a-menu-on-the-ide-menu-bar"></a>Creazione di un Menu nella barra dei Menu dell'IDE

#### <a name="to-create-a-menu"></a>Per creare un menu

1. Nelle **Esplora soluzioni**, aprire TestCommandPackage.vsct.

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

4. Trovare il `Buttons` sezione. Si noti che il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] modello di pacchetto ha generato una `Button` elemento con il relativo elemento padre impostata su `MyMenuGroup`. Di conseguenza, questo comando verrà visualizzato nel menu.

## <a name="building-and-testing-the-extension"></a>Compilazione e l'estensione per il Testing

1. Compilare il progetto e avviare il debug. Un'istanza dell'istanza sperimentale dovrebbe essere visualizzato.

2. Barra dei menu nell'istanza sperimentale dovrebbe contenere una **TestMenu** menu.

3. Nel **TestMenu** menu, fare clic su **richiamare comandi Test**.

     Una finestra di messaggio dovrà essere visualizzato e visualizzare il messaggio "TestCommand pacchetto all'interno di TopLevelMenu.TestCommand.MenuItemCallback()". Ciò indica che il nuovo comando funziona.

## <a name="see-also"></a>Vedere anche
 [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)
