---
title: 'Procedura dettagliata: Aggiunta di CODICE XAML personalizzato alla pagina iniziale | Microsoft Docs'
description: Informazioni su come creare una pagina Visual Studio iniziale che contiene un Web browser usando questa procedura dettagliata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 4da513c5040b6da97a9a545b5b40892d8cdc4c30
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158047"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>Procedura dettagliata: Aggiungere codice XAML personalizzato alla pagina iniziale

Questa procedura dettagliata illustra come creare una pagina iniziale Visual Studio personalizzata che contiene un Web browser.

## <a name="add-custom-xaml"></a>Aggiungere codice XAML personalizzato

1. Creare una pagina iniziale seguendo le istruzioni riportate in [Creare una pagina iniziale personalizzata](../extensibility/creating-a-custom-start-page.md).

2. Nel file *MainWindow.xaml* individuare la \<Grid> sezione .

3. Aggiungere un \<TabControl> elemento e un elemento \<TabItem> all'interno \< Grid> dell'elemento , come illustrato nell'esempio seguente.

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

4. Aggiungere un secondo \<TabItem> elemento , con un elemento che apre un nuovo \<Button> progetto:

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

     Verrà aperta l'istanza sperimentale Visual Studio, con la pagina iniziale personalizzata installata ma non selezionata.

2. Nell'istanza sperimentale di Visual Studio aprire la **pagina Strumenti /Opzioni/Ambiente.**

3. Selezionare **Avvio**. **Nell'elenco Personalizza pagina iniziale** selezionare il file con estensione *xaml* e fare clic su **OK.**

4. Scegliere **Pagina iniziale** dal menu **Visualizza**.

5. Fare clic **sulla Bing** di connessione.

     Verrà visualizzata una Bing Web.

6. Fare clic **sulla scheda MyButton.**

     Verrà visualizzato un pulsante **MyProject** che apre la **finestra di dialogo Nuovo Project** progetto.

7. Chiudere l'istanza sperimentale.

Per applicare la pagina iniziale personalizzata, in **Strumenti**  >  **Opzioni**  >  **Ambiente** selezionare **Avvio**. **Nell'elenco Personalizza pagina iniziale** selezionare il file con estensione *xaml* e fare clic su **OK.**

## <a name="next-steps"></a>Passaggi successivi

La Visual Studio iniziale contiene ora una scheda che visualizza una scheda Web browser e una scheda MyButton. È possibile creare pagine di avvio personalizzate con altre funzionalità usando il modello *code-behind* per aggiungere un .dll personalizzato, come illustrato in Aggiunta del controllo utente [alla pagina iniziale](../extensibility/adding-user-control-to-the-start-page.md). È possibile condividere pagine di avvio personalizzate con altri utenti pubblicando il file vsix risultante nel sito Web [di Visual Studio Marketplace](https://marketplace.visualstudio.com/) o in un altro sito Web o condivisione di rete. Per altre informazioni, vedere [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md).

## <a name="see-also"></a>Vedi anche

- [Personalizzare la pagina iniziale](../ide/customizing-the-start-page-for-visual-studio.md)
- [Controlli contenitore WPF](/previous-versions/bb675291(v=vs.110))