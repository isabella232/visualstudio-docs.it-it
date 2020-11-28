---
title: 'Procedura: contrassegnare i controlli come controlli sicuri | Microsoft Docs'
description: Contrassegnare i controlli come controlli sicuri nella proprietà voci di controllo sicure di un elemento di progetto SharePoint o in Progettazione pacchetti quando si aggiunge un assembly.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 024cd50fc36b84addca11dc3c0f23cdc64fa507d
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304508"
---
# <a name="how-to-mark-controls-as-safe-controls"></a>Procedura: contrassegnare i controlli come controlli sicuri
  Per la sicurezza, SharePoint distingue tra i controlli Web protetti da attacchi di script injection e Web che non lo sono. È possibile accedere ai controlli protetti o ai *controlli sicuri* da parte di utenti non attendibili. È possibile contrassegnare i controlli come sicuri nella proprietà voci di controllo sicure di un elemento del progetto SharePoint o in **Progettazione pacchetti** quando si aggiunge un assembly al pacchetto. Per ulteriori informazioni, vedere

- [web.config le impostazioni del file cambiano](/previous-versions/office/developer/sharepoint-2007/bb802890(v=office.12)) e [la registrazione di un assembly Web part come controllo sicuro](/previous-versions/office/developer/sharepoint2003/dd587360(v=office.11)).

> [!IMPORTANT]
> Queste procedure sono a scopo illustrativo. Contrassegnare i controlli in modo sicuro solo se si è certi che siano protetti.

## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>Contrassegno di controlli sicuri nella proprietà voci di controllo sicure

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>Per contrassegnare i controlli come sicuri o non sicuri nella proprietà voci di controllo sicure

1. Creare una soluzione di SharePoint con un progetto Web part visiva.

2. Aggiungere due controlli alla web part, ovvero una casella di testo e un pulsante. Lasciare i nomi rispettivamente come valori predefiniti, TextBox1 e Button1.

3. Aggiungere due voci alla proprietà delle voci di **controllo sicure** della web part. A tale scopo, scegliere il pulsante con i puntini di sospensione (![ASP.NET Mobile Designer ellisse](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")) accanto alla proprietà **voci di controllo sicure** nella finestra **proprietà** .

     Verrà visualizzata la finestra di dialogo **voci di controllo sicure** .

4. Nella finestra di dialogo **voci di controllo sicure** scegliere il pulsante **Aggiungi** due volte per aggiungere due voci di controllo sicure al riquadro **membri** : una per il pulsante e una per la casella di testo.

5. Scegliere la prima voce di controllo sicura, quindi impostare il valore della relativa proprietà **Safe** su **false**, la **proprietà nome tipo** su **Button1** e la relativa proprietà **Safe su script** su **false**.

     Questo passaggio identifica il controllo Button come un controllo unsafe.

6. Scegliere la seconda voce di controllo sicura nell'elenco. Lasciare **true** il valore della proprietà **Safe** e impostare la relativa proprietà **Type Name** su **textBox1** e la relativa proprietà **safe against script** su **true**.

     Il controllo casella di testo è ora contrassegnato come controllo protetto da attacchi di script injection.

7. Scegliere il pulsante **OK** per chiudere la finestra di dialogo.

## <a name="marking-safe-controls-in-the-package-designer"></a>Contrassegno di controlli sicuri in Progettazione pacchetti

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>Per contrassegnare i controlli come sicuri o non sicuri in Progettazione pacchetti

1. Creare una soluzione di SharePoint con un progetto Web part visiva.

2. Aggiungere due controlli alla web part, ovvero una casella di testo e un pulsante. Lasciare i nomi rispettivamente come valori predefiniti, TextBox1 e Button1.

     Prendere nota dello spazio dei nomi del controllo perché verrà usato in un secondo momento.

3. Sulla barra dei menu scegliere **Compila**  >  **Compila soluzione** per compilare il progetto.

4. Creare un'altra soluzione SharePoint.

5. In **Esplora soluzioni** aprire il menu di scelta rapida per il file *Package. Package* , quindi scegliere **Apri** per aprire **Progettazione pacchetti**.

6. In **Progettazione pacchetti** scegliere la scheda **Avanzate** .

7. In **assembly aggiuntivi** scegliere il pulsante **Aggiungi** , quindi scegliere **Aggiungi assembly esistente** dall'elenco.

8. Nella finestra di dialogo **Aggiungi assembly esistente** scegliere il pulsante con i puntini di sospensione (![ASP.NET Mobile Designer ellisse](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")) accanto a **percorso di origine**.

9. Scegliere l'assembly dalla soluzione SharePoint creata nel passaggio 1, quindi scegliere il pulsante **Apri** .

10. Per questo esempio, lasciare l'opzione della **destinazione di distribuzione** come GlobalAssemblyCache.

     Questo passaggio determina la distribuzione dell'assembly nella global assembly cache (GAC) di sistema. Se si desidera che l'assembly venga distribuito nella cartella dell'applicazione Web (bin), selezionare tale opzione. Per ulteriori informazioni, vedere [distribuzione di Web part in SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14)).

11. Nella casella **controlli sicuri** scegliere il pulsante **fare clic qui per aggiungere un nuovo elemento** .

12. Immettere i valori per le proprietà della tabella seguente.

    |Nome proprietà|valore|
    |-------------------|-----------|
    |Spazio dei nomi|Spazio dei nomi completo per il controllo, ad esempio **BdcModelProject1. VisualWebPart1**.|
    |Nome tipo|Button1|
    |Nome assembly|Un nome di assembly sicuro, ad esempio: Microsoft. Office. SharePoint. ClientExtensions, Version = 14.0.0.0, Culture = neutral, PublicKeyToken = 71e9bce111e9429c.|
    |Safe|Deselezionare la casella di controllo **sicurezza** .|
    |Sicurezza dallo script|Lasciare la casella di controllo non crittografata per **script** .|

    > [!NOTE]
    > Il valore del **nome dell'assembly** per gli assembly aggiunti tramite la scheda **Avanzate** della finestra di **progettazione del pacchetto** non può essere un token, ma deve essere un assembly con nome sicuro. Per altre informazioni, vedere [Creazione e utilizzo degli assembly con nome sicuro](/previous-versions/dotnet/netframework-4.0/xwb8f617(v=vs.100)).

13. Premere il tasto **Tab** per creare un'altra voce di controllo sicura.

14. Scegliere di nuovo il pulsante **fare clic qui per aggiungere un nuovo elemento** .

15. Immettere i valori per le proprietà della tabella seguente.

    |Nome proprietà|valore|
    |-------------------|-----------|
    |Spazio dei nomi|Spazio dei nomi completo per il controllo, ad esempio **BdcModelProject1. VisualWebPart1**.|
    |Nome tipo|TextBox1|
    |Nome assembly|Un nome di assembly sicuro, ad esempio: Microsoft. Office. SharePoint. ClientExtensions, Version = 14.0.0.0, Culture = neutral, PublicKeyToken = 71e9bce111e9429c.|
    |Safe|Selezionare la casella di controllo **Safe** .|
    |Sicurezza dallo script|Selezionare la casella di controllo protezione da **script** .|

16. Premere il tasto **Tab** , quindi scegliere il pulsante **OK** per chiudere la finestra di dialogo.

## <a name="see-also"></a>Vedere anche
- [Fornire informazioni sulla creazione di pacchetti e sulla distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Pacchetto e distribuzione di soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
