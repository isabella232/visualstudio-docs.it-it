---
title: Connettersi ai dati in un database di Access
description: Informazioni su come connettersi ai dati in un database di Access, ovvero un file con estensione mdb o accdb. file, in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 07/18/2019
ms.topic: how-to
helpviewer_keywords:
- data [Visual Studio], connecting
- connecting to data, Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 156acfd56789ec13201738e72c6df283e257e94f
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436862"
---
# <a name="connect-to-data-in-an-access-database"></a>Connettersi ai dati in un database di Access

È possibile connettersi a un database di Access, ovvero un file con estensione *MDB* o *accdb* , usando Visual Studio. Dopo avere definito la connessione, i dati vengono visualizzati nella finestra **Origine dati** Da qui è possibile trascinare tabelle o viste nell'area di progettazione.

## <a name="prerequisites"></a>Prerequisiti

Per usare queste procedure, è necessario un progetto Windows Forms o WPF e un database di Access (file con estensione *accdb* ) o un database di Access 2000-2003 (file con *estensione mdb* ). Attenersi alla procedura che corrisponde al tipo di file utilizzato.

## <a name="create-a-dataset-for-an-accdb-file"></a>Creare un set di dati per un file con estensione accdb

Connettersi ai database creati con Microsoft 365, Access 2013, Access 2010 o Access 2007 utilizzando la procedura riportata di seguito.

1. Aprire un progetto di applicazione Windows Forms o WPF in Visual Studio.

2. Per aprire la finestra **origini dati** , scegliere altre **View** **Other Windows**  >  **origini dati** di Windows dal menu Visualizza.

   ![Visualizza, Altre finestre, Origini dati](../data-tools/media/viewdatasources.png)

3. Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.

   Verrà avviata la **Configurazione guidata origine dati** .

4. Selezionare **database** nella pagina **scegliere un tipo di origine dati** e quindi fare clic su **Avanti**.

5. Selezionare **DataSet** nella pagina **scegliere un modello di database** e quindi fare clic su **Avanti**.

6. Nella pagina **Seleziona connessione dati** selezionare **Nuova connessione** per configurare una nuova connessione dati.

   Verrà visualizzata la finestra di dialogo **Aggiungi connessione**.

7. Se l' **origine dati** non è impostata su **file di database Microsoft Access** , selezionare il pulsante **Cambia** .

   Verrà visualizzata la finestra di dialogo **Modifica origine dati** . Nell'elenco delle origini dati scegliere file di **database Microsoft Access**. Nell'elenco a discesa **provider di dati** selezionare **.NET Framework provider di dati per OLE DB** , quindi scegliere **OK**.

8. Scegliere **Sfoglia** accanto a **nome file di database** , quindi passare al file con estensione *accdb* e scegliere **Apri**.

9. Immettere un nome utente e una password, se necessario, quindi scegliere **OK**.

10. Nella pagina **scegliere la connessione dati** selezionare **Avanti** .

    È possibile che venga visualizzata una finestra di dialogo che informa che il file di dati non è presente nel progetto corrente. Selezionare **Sì** o **No**.

11. Selezionare **Avanti** nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione** .

12. Espandere il nodo **Tabelle** nella pagina **Seleziona oggetti di database**.

13. Selezionare le tabelle o le viste che si desidera includere nel set di dati e quindi fare clic su **fine**.

    Il dataset viene aggiunto al progetto e le tabelle e le viste vengono visualizzate nella finestra **Origini dati**.

## <a name="create-a-dataset-for-an-mdb-file"></a>Creare un set di dati per un file con estensione mdb

Connettersi ai database creati con Access 2000-2003 usando la procedura seguente.

1. Aprire un progetto di applicazione Windows Forms o WPF in Visual Studio.

2. Scegliere altre **View** **Other Windows**  >  **origini dati** di Windows dal menu Visualizza.

   ![Visualizza, Altre finestre, Origini dati](../data-tools/media/viewdatasources.png)

3. Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.

    Verrà avviata la **Configurazione guidata origine dati** .

4. Selezionare **database** nella pagina **scegliere un tipo di origine dati** e quindi fare clic su **Avanti**.

5. Selezionare **DataSet** nella pagina **scegliere un modello di database** e quindi fare clic su **Avanti**.

6. Nella pagina **Seleziona connessione dati** selezionare **Nuova connessione** per configurare una nuova connessione dati.

7. Se l'origine dati non è **un file di database Microsoft Access (OLE DB)** , selezionare **Cambia** per aprire la finestra di dialogo **Modifica origine dati** e selezionare **file di database Microsoft Access** , quindi scegliere **OK**.

8. Nel **nome del file di database** specificare il percorso e il nome del file con *estensione mdb* a cui si desidera connettersi e quindi fare clic su **OK**.

   ![Aggiunta della connessione al file di database di Access](../data-tools/media/add-connection-access-db.png)

9. Nella pagina **scegliere la connessione dati** selezionare **Avanti** .

10. Selezionare **Avanti** nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione** .

11. Espandere il nodo **Tabelle** nella pagina **Seleziona oggetti di database**.

12. Selezionare le tabelle o le viste desiderate nel set di dati e quindi fare clic su **fine**.

    Il dataset viene aggiunto al progetto e le tabelle e le viste vengono visualizzate nella finestra **Origini dati**.

## <a name="next-steps"></a>Passaggi successivi

Il set di dati appena creato è disponibile nella finestra **origini dati** . A questo punto è possibile eseguire una delle attività seguenti:

- Selezionare gli elementi nella finestra **origini dati** e trascinarli nel form o nell'area di progettazione. vedere [associare Windows Forms controlli ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) o [WPF Data Binding Overview](/dotnet/desktop-wpf/data/data-binding-overview)).

- Aprire l'origine dati in **Progettazione DataSet** per aggiungere o modificare gli oggetti che costituiscono il set di dati.

- Aggiungere la logica di convalida <xref:System.Data.DataTable.ColumnChanging> all' <xref:System.Data.DataTable.RowChanging> evento o delle tabelle dati nel DataSet (vedere [convalidare i dati nei set di dati](../data-tools/validate-data-in-datasets.md)).

## <a name="see-also"></a>Vedere anche

- [Aggiungere connessioni](../data-tools/add-new-connections.md)
- [Panoramica di data binding WPF](/dotnet/framework/wpf/data/data-binding-overview)
- [Windows Forms data binding](/dotnet/framework/winforms/data-binding-and-windows-forms)
