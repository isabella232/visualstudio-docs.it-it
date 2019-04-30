---
title: 'Procedura: Contrassegnare i controlli come controlli sicuri | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- SharePoint development in Visual Studio, advanced packaging tools
- safe controls [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 30bb597288c19328bb71ce7b5212200991d7181e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443077"
---
# <a name="how-to-mark-controls-as-safe-controls"></a>Procedura: Contrassegnare i controlli come controlli sicuri
  Per la sicurezza, SharePoint consente di distinguere tra i controlli Web che sono protetti dagli attacchi script injection e Web che non sono. Protetto (controlli), oppure *controlli sicuri*, sono accessibili da utenti non attendibili. È possibile contrassegnare i controlli come sicuri nella proprietà di un elemento di progetto SharePoint o in voci di controllo sicure le **Progettazione pacchetti** quando si aggiunge un assembly al pacchetto. Per altre informazioni, vedere

- [Modifica delle impostazioni Web. config](http://go.microsoft.com/fwlink/?LinkId=178965) e [la registrazione di un Assembly della Web Part come SafeControl](http://go.microsoft.com/fwlink/?LinkId=171013).

> [!IMPORTANT]
> Queste procedure sono per solo a scopo illustrativo. Contrassegnare i controlli sicuri solo se si è certi che siano protetti.

## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>Contrassegnare i controlli sicuri nella proprietà voci SafeControl

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>Per contrassegnare i controlli come safe o unsafe nella proprietà voci SafeControl

1. Creare una soluzione di SharePoint con un progetto di Web Part visiva.

2. Aggiungere due controlli alla Web part: una casella di testo e un pulsante. Lasciare i nomi dei valori predefiniti, TextBox1 e Button1, rispettivamente.

3. Aggiungere due voci per la Web part **voci di controllo sicure** proprietà. A tale scopo, scegliere i puntini di sospensione (![ellisse di ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ellisse di ASP.NET Mobile Designer")) accanto al pulsante il **voci di controllo sicure** proprietà nel  **Proprietà** finestra.

     Il **voci di controllo sicure** verrà visualizzata la finestra di dialogo.

4. Nel **voci di controllo sicure** finestra di dialogo scegliere la **Add** due volte per aggiungere due voci di controllo sicure per il **membri** riquadro: uno per il pulsante e una casella di testo.

5. Scegliere la prima voce di controllo sicura e quindi modificare il valore di relativi **sicuro** proprietà **False**, la relativa **nome del tipo** proprietà **Button1**e il relativo **sicurezza Script** alla proprietà **False**.

     Questo passaggio identifica il controllo pulsante come controllo di tipo unsafe.

6. Scegliere la seconda voce di controllo sicura nell'elenco. Lasciare il valore della relativa **sicuro** proprietà come **True** e impostare relativo **nome del tipo** proprietà **TextBox1** e il relativo **sicuro Script** proprietà **True**.

     Controllo casella di testo è ora contrassegnato come un controllo che è protetto dagli attacchi script injection.

7. Scegliere il pulsante **OK** per chiudere la finestra di dialogo.

## <a name="marking-safe-controls-in-the-package-designer"></a>Contrassegnare i controlli sicuri nella progettazione dei pacchetti

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>Per contrassegnare i controlli come safe o unsafe nella progettazione dei pacchetti

1. Creare una soluzione di SharePoint con un progetto di Web Part visiva.

2. Aggiungere due controlli alla Web part: una casella di testo e un pulsante. Lasciare i nomi dei valori predefiniti, TextBox1 e Button1, rispettivamente.

     Prendere nota dello spazio dei nomi del controllo perché viene utilizzato in un secondo momento.

3. Nella barra dei menu, scegliere **compilare** > **Compila soluzione** per compilare il progetto.

4. Creare un'altra soluzione di SharePoint.

5. Nella **Esplora soluzioni**, aprire il menu di scelta rapida per il *package. package* del file e quindi scegliere **aprire** per aprire la **Progettazione pacchetti**.

6. Nel **Progettazione pacchetti**, scegliere il **avanzate** scheda.

7. Sotto **Additional Assemblies**, scegliere il **Add** pulsante e quindi scegliere **Aggiungi Assembly esistente** dall'elenco.

8. Nel **Aggiungi Assembly esistente** finestra di dialogo scegliere i puntini di sospensione (![ellisse di ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ellisse di ASP.NET Mobile Designer")) accanto al pulsante  **Percorso di origine**.

9. Scegliere l'assembly dalla soluzione di SharePoint creato nel passaggio 1 e quindi scegliere il **aperto** pulsante.

10. Per questo esempio, lasciare il **destinazione distribuzione** opzione GlobalAssemblyCache.

     Questo passaggio fa sì che l'assembly distribuire il sistema Global Assembly Cache (GAC). Se si desidera che l'assembly per la distribuzione della cartella di Web application (Bin), selezionare l'opzione corrispondente. Per altre informazioni, vedere [distribuzione di Web part in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177509).

11. Nel **controlli sicuri** scegliere i **fare clic qui per aggiungere un nuovo elemento** pulsante.

12. Immettere i valori per le proprietà contenute nella tabella seguente.

    |Nome proprietà|Value|
    |-------------------|-----------|
    |Spazio dei nomi|Il nome completo dello spazio dei nomi per il controllo, ad esempio **BdcModelProject1.VisualWebPart1**.|
    |Nome tipo|Button1|
    |Nome assembly|Nome di assembly sicuro, ad esempio: Microsoft.Office.SharePoint.ClientExtensions, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c.|
    |Safe|Cancella il **sicuro** casella di controllo.|
    |Sicurezza Script|Lasciare il **sicurezza Script** casella di controllo.|

    > [!NOTE]
    > Il **nome dell'Assembly** valore degli assembly aggiunti tramite il **avanzate** scheda della finestra del **Progettazione pacchetti** non è un token, deve essere un assembly con nome sicuro. Per altre informazioni, vedere [Creazione e utilizzo degli assembly con nome sicuro](http://go.microsoft.com/fwlink/?LinkId=177513).

13. Scegliere il **scheda** tasto per creare un'altra voce di controllo sicura.

14. Scegliere il **fare clic qui per aggiungere un nuovo elemento** nuovamente clic sul pulsante.

15. Immettere i valori per le proprietà contenute nella tabella seguente.

    |Nome proprietà|Value|
    |-------------------|-----------|
    |Spazio dei nomi|Il nome completo dello spazio dei nomi per il controllo, ad esempio **BdcModelProject1.VisualWebPart1**.|
    |Nome tipo|TextBox1|
    |Nome assembly|Nome di assembly sicuro, ad esempio: Microsoft.Office.SharePoint.ClientExtensions, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c.|
    |Safe|Selezionare il **sicuro** casella di controllo.|
    |Sicurezza Script|Selezionare il **sicurezza Script** casella di controllo.|

16. Scegliere il **della scheda** chiave e quindi scegliere il **OK** per chiudere la finestra di dialogo.

## <a name="see-also"></a>Vedere anche
- [Fornire le informazioni di creazione di pacchetti e distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
