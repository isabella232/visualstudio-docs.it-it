---
title: Connettersi ai dati in un database di Access
description: Informazioni su come connettersi ai dati in un database di Access (un file con estensione mdb o accdb.file) in Visual Studio.
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
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b8280c29649a792839e2bc18a409e76f276b71e4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631541"
---
# <a name="connect-to-data-in-an-access-database"></a>Connettersi ai dati in un database di Access

È possibile connettersi a un database di Access (un file con estensione *mdb* o *accdb)* usando Visual Studio. Dopo avere definito la connessione, i dati vengono visualizzati nella finestra **Origine dati** Da qui è possibile trascinare tabelle o viste nell'area di progettazione.

## <a name="prerequisites"></a>Prerequisiti

Per usare queste procedure, è necessario un progetto Windows Forms o WPF e un database di Access (file con estensione *accdb)* o un database di Access 2000-2003 (file con estensione *mdb).* Attenersi alla procedura che corrisponde al tipo di file utilizzato.

## <a name="create-a-dataset-for-an-accdb-file"></a>Creare un set di dati per un file con estensione accdb

Connessione ai database creati con Microsoft 365, Access 2013, Access 2010 o Access 2007 usando la procedura seguente.

1. Aprire un progetto Windows Form o applicazione WPF in Visual Studio.

2. Per aprire la **finestra Origini** dati, **scegliere** Altre origini dati dal menu Visualizza Windows   >  **dati**.

   ![Visualizza, Altre finestre, Origini dati](../data-tools/media/viewdatasources.png)

3. Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.

   Verrà **visualizzata la Configurazione guidata origine** dati.

4. Selezionare **Database** nella **pagina Scegliere un tipo di origine** dati e quindi selezionare **Avanti.**

5. Selezionare **Set** di dati **nella pagina Scegliere un modello di** database e quindi selezionare **Avanti.**

6. Nella pagina **Seleziona connessione dati** selezionare **Nuova connessione** per configurare una nuova connessione dati.

   Verrà visualizzata la finestra di dialogo **Aggiungi connessione**.

7. Se **l'opzione** Origine dati non è impostata su **File di database di Microsoft Access**, selezionare il **pulsante** Modifica .

   Verrà **visualizzata la finestra di dialogo** Modifica origine dati . Nell'elenco delle origini dati scegliere File **di database di Microsoft Access.** **Nell'elenco a** discesa Provider di dati **selezionare .NET Framework provider di dati per OLE DB** e quindi scegliere **OK.**

8. Scegliere **Sfoglia** accanto a **Nome file di database,** quindi passare al file con estensione *accdb* e scegliere **Apri.**

9. Immettere un nome utente e una password (se necessario) e quindi scegliere **OK.**

10. Selezionare **Avanti** nella **pagina Scegliere la connessione** dati.

    È possibile che venga visualizzata una finestra di dialogo che indica che il file di dati non è presente nel progetto corrente. Selezionare **Sì** o **No.**

11. Selezionare **Avanti** nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione.**

12. Espandere il nodo **Tabelle** nella pagina **Seleziona oggetti di database**.

13. Selezionare le tabelle o le viste da includere nel set di dati e quindi selezionare **Fine.**

    Il dataset viene aggiunto al progetto e le tabelle e le viste vengono visualizzate nella finestra **Origini dati**.

## <a name="create-a-dataset-for-an-mdb-file"></a>Creare un set di dati per un file con estensione mdb

Connessione ai database creati con Access 2000-2003 usando la procedura seguente.

1. Aprire un progetto Windows Form o applicazione WPF in Visual Studio.

2. Scegliere **Altre** origini dati dal menu **Visualizza Windows**  >  **dati .**

   ![Visualizza, Altre finestre, Origini dati](../data-tools/media/viewdatasources.png)

3. Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.

    Verrà **visualizzata la Configurazione guidata origine** dati.

4. Selezionare **Database** nella **pagina Scegliere un tipo di origine** dati e quindi selezionare **Avanti.**

5. Selezionare **Set** di dati **nella pagina Scegliere un modello di** database e quindi selezionare **Avanti.**

6. Nella pagina **Seleziona connessione dati** selezionare **Nuova connessione** per configurare una nuova connessione dati.

7. Se l'origine dati non è File di database  di Microsoft  **Access (OLE DB),** selezionare Cambia per aprire la finestra di dialogo Modifica origine dati e selezionare File di database di **Microsoft Access** e quindi **selezionare OK.**

8. In **Nome file di database** specificare il percorso e il nome del file con estensione *mdb* a cui connettersi e quindi selezionare **OK.**

   ![Aggiunta della connessione al file di database di Access](../data-tools/media/add-connection-access-db.png)

9. Selezionare **Avanti** nella **pagina Scegliere la connessione** dati.

10. Selezionare **Avanti** nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione.**

11. Espandere il nodo **Tabelle** nella pagina **Seleziona oggetti di database**.

12. Selezionare le tabelle o le viste desiderate nel set di dati e quindi selezionare **Fine.**

    Il dataset viene aggiunto al progetto e le tabelle e le viste vengono visualizzate nella finestra **Origini dati**.

## <a name="next-steps"></a>Passaggi successivi

Il set di dati appena creato è disponibile nella **finestra Origini** dati. A questo punto è possibile eseguire una delle attività seguenti:

- Selezionare gli  elementi nella finestra Origini dati e trascinarli nel form o nell'area di progettazione (vedere Associare i controlli Windows Forms ai dati [in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) o WPF [data binding panoramica).](/dotnet/desktop-wpf/data/data-binding-overview)

- Aprire l'origine dati in **Progettazione DataSet** per aggiungere o modificare gli oggetti che costituiscono il set di dati.

- Aggiungere la logica di convalida all'evento o delle tabelle di dati nel set di dati <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> (vedere [Convalidare i dati nei set di dati).](../data-tools/validate-data-in-datasets.md)

## <a name="see-also"></a>Vedi anche

- [Aggiungere connessioni](../data-tools/add-new-connections.md)
- [Panoramica data binding WPF](/dotnet/framework/wpf/data/data-binding-overview)
- [Windows Moduli data binding](/dotnet/framework/winforms/data-binding-and-windows-forms)
