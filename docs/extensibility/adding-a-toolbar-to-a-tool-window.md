---
title: Aggiunta di una barra degli strumenti a una finestra degli strumenti | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3eefb192c5e0ec660a614af8c32ecc34cc683888
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53934427"
---
# <a name="add-a-toolbar-to-a-tool-window"></a>Aggiungere una barra degli strumenti a una finestra degli strumenti
Questa procedura dettagliata illustra come aggiungere una barra degli strumenti a una finestra degli strumenti.  
  
 Una barra degli strumenti è visualizzata una striscia orizzontale o verticale che contiene i pulsanti associati a comandi. La lunghezza di una barra degli strumenti in una finestra degli strumenti è sempre identico alla larghezza o all'altezza della finestra degli strumenti, a seconda della posizione di ancoraggio la barra degli strumenti.  
  
 A differenza delle barre degli strumenti nell'IDE, una barra degli strumenti in una finestra degli strumenti deve essere ancorato e non può essere spostato o personalizzato. Se il pacchetto VSPackage è scritto in codice umanaged, la barra degli strumenti può essere ancorato a qualsiasi lato.  
  
 Per altre informazioni su come aggiungere una barra degli strumenti, vedere [aggiunta di una barra degli strumenti](../extensibility/adding-a-toolbar.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-toolbar-for-a-tool-window"></a>Creare una barra degli strumenti per una finestra degli strumenti  
  
1.  Creare un progetto VSIX denominato `TWToolbar` che ha entrambi un comando di menu denominato **TWTestCommand** e una finestra degli strumenti denominata **TestToolWindow**. Per altre informazioni, vedere [creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md) e [creare un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md). È necessario aggiungere il modello di elemento di comando prima di aggiungere il modello di finestra degli strumenti.  
  
2.  Nelle *TWTestCommandPackage.vsct*, cercare la sezione di simboli. Nel nodo GuidSymbol denominato guidTWTestCommandPackageCmdSet dichiarare una barra degli strumenti e un gruppo della barra degli strumenti, come indicato di seguito.  
  
    ```xml  
    <IDSymbol name="TWToolbar" value="0x1000" />  
    <IDSymbol name="TWToolbarGroup" value="0x1050" />  
    ```  
  
3.  In cima il `Commands` sezione, creare un `Menus` sezione. Aggiungere un `Menu` elemento per definire la barra degli strumenti.  
  
    ```xml  
    <Menus>  
        <Menu guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" type="ToolWindowToolbar">  
            <CommandFlag>DefaultDocked</CommandFlag>  
            <Strings>  
                <ButtonText>Test Toolbar</ButtonText>  
                <CommandName>Test Toolbar</CommandName>  
            </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
     Le barre degli strumenti non possono essere annidati, come sottomenu. Pertanto, non è necessario assegnare un elemento padre. Inoltre, non è necessario impostare la priorità, perché l'utente può spostare barre degli strumenti. In genere, la posizione iniziale di una barra degli strumenti è definita a livello di codice, ma le successive modifiche dall'utente vengono rese persistenti.  
  
4.  Nella sezione Groups, definire un gruppo per contenere i comandi per la barra degli strumenti.  
  
    ```xml  
  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />  
    </Group>  
    ```  
  
5.  Nella sezione pulsanti, cambiare l'elemento padre dell'elemento pulsante esistente al gruppo della barra degli strumenti in modo che verrà visualizzata la barra degli strumenti.  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke TWTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     Per impostazione predefinita, se una barra degli strumenti non dispone di alcun comando, non visualizzato.  
  
     Poiché la nuova barra degli strumenti non viene aggiunto automaticamente alla finestra degli strumenti, è necessario aggiungere in modo esplicito la barra degli strumenti. Questo è discusso nella sezione seguente.  
  
## <a name="add-the-toolbar-to-the-tool-window"></a>Aggiungere la barra degli strumenti alla finestra degli strumenti  
  
1.  Nelle *TWTestCommandPackageGuids.cs* aggiungere le righe seguenti.  
  
    ```csharp  
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const int TWToolbar = 0x1000;  
    ```  
  
2.  Nelle *TestToolWindow.cs* aggiungere la seguente istruzione using.  
  
    ```csharp  
    using System.ComponentModel.Design;  
    ```  
  
3.  Aggiungere la riga seguente nel costruttore TestToolWindow.  
  
    ```csharp  
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);  
    ```  
  
## <a name="test-the-toolbar-in-the-tool-window"></a>Testare la barra degli strumenti nella finestra degli strumenti  
  
1.  Compilare il progetto e avviare il debug. L'istanza sperimentale di Visual Studio dovrebbe essere visualizzato.  
  
2.  Nel **visualizzazione / Other Windows** menu, fare clic su **ToolWindow Test** per visualizzare la finestra degli strumenti.  
  
     Verrà visualizzata una barra degli strumenti (sembra che l'icona predefinita) nella parte superiore sinistra della finestra degli strumenti, appena sotto il titolo.  
  
3.  Sulla barra degli strumenti, fare clic sull'icona per visualizzare il messaggio **TWTestCommandPackage all'interno di TWToolbar.TWTestCommand.MenuItemCallback()**.  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere una barra degli strumenti](../extensibility/adding-a-toolbar.md)