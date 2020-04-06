---
title: 'Procedura dettagliata: Aggiunta di codice XAML personalizzato alla pagina iniziale . Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 4e2afc90dc96978e8a8290afaa2d3278e8b621b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697685"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>Procedura dettagliata: Aggiungere codice XAML personalizzato alla pagina inizialeWalkthrough: Add custom XAML to the start page

In questa procedura dettagliata viene illustrato come creare una pagina iniziale personalizzata di Visual Studio che contiene un Web browser.

## <a name="add-custom-xaml"></a>Aggiungere codice XAML personalizzato

1. Creare una pagina iniziale seguendo le istruzioni in [Creare una pagina iniziale personalizzata.](../extensibility/creating-a-custom-start-page.md)

2. Nel file *MainWindow.xaml* individuare \<la sezione Grid>.

3. Aggiungere \<un elemento TabControl \<> e \< un> elemento TabItem all'interno dell'elemento Grid>, come illustrato nell'esempio seguente.

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

4. Aggiungere un \<secondo tabItem \<>, con un Button> elemento che apre un nuovo progetto:Add a second TabItem>, with a Button> element that opens a new project:

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="MyButton" Height="Auto">
                <Button Name="btnNewProj" Content="New Project"
                    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
                    CommandParameter="File.NewProject" >
                </Button>
            </TabItem>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

## <a name="test-the-custom-start-page"></a>Testare la pagina iniziale personalizzata

1. Premere **F5**.

     Viene aperta l'istanza sperimentale di Visual Studio, con la pagina iniziale personalizzata installata ma non selezionata.

2. Nell'istanza sperimentale di Visual Studio, aprire il **Strumenti /Opzioni / Ambiente** pagina.

3. Selezionare **Avvio**. Nell'elenco **Personalizza pagina iniziale** selezionare il file *con estensione xaml* e fare clic su **OK**.

4. Scegliere **Pagina iniziale** dal menu **Visualizza**.

5. Fare clic sulla scheda **Bing.**

     Verrà visualizzata una pagina Web di Bing.You should see a Bing web page.

6. Fare clic sulla scheda **MyButton.**

     Verrà visualizzato un pulsante **MyProject,** che apre la finestra di dialogo **Nuovo progetto.**

7. Chiudere l'istanza sperimentale.

Per applicare la pagina iniziale personalizzata, in**Ambiente****opzioni** >  **strumenti** > selezionare **Avvio**. Nell'elenco **Personalizza pagina iniziale** selezionare il file *con estensione xaml* e fare clic su **OK**.

## <a name="next-steps"></a>Passaggi successivi

La pagina iniziale di Visual Studio contiene ora una scheda che visualizza una scheda del browser Web e una scheda MyButton. È possibile creare pagine iniziali personalizzate con altre funzionalità utilizzando il modello *code-behind* per aggiungere una DLL personalizzata, come illustrato in Aggiunta del [controllo utente alla pagina iniziale](../extensibility/adding-user-control-to-the-start-page.md). È possibile condividere pagine iniziali personalizzate con altri utenti pubblicando il file VSIX risultante nel sito Web di [Visual Studio Marketplace](https://marketplace.visualstudio.com/) o in un altro sito Web o condivisione di rete. Per altre informazioni, vedere [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md).

## <a name="see-also"></a>Vedere anche

- [Personalizzare la pagina iniziale](../ide/customizing-the-start-page-for-visual-studio.md)
- [Controlli contenitore WPFWPF container controls](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)
