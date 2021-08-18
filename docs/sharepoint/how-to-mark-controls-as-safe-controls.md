---
title: 'Procedura: Contrassegnare i controlli come Cassaforte controlli | Microsoft Docs'
description: Contrassegnare i controlli come controlli sicuri nella proprietà Cassaforte Control Entries di un elemento di progetto SharePoint o in Progettazione pacchetti quando si aggiunge un assembly.
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: e96a27be0ae8a71125964e27da99270d9142886c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092982"
---
# <a name="how-to-mark-controls-as-safe-controls"></a>Procedura: Contrassegnare i controlli come controlli sicuri
  Per motivi di sicurezza, SharePoint i controlli Web protetti da script injection e i controlli Web che non lo sono. I controlli protetti, *o controlli sicuri,* sono accessibili a utenti non attendibili. È possibile contrassegnare i controlli come sicuri nella proprietà Cassaforte Control Entries  di un elemento di progetto SharePoint o in Progettazione pacchetti quando si aggiunge un assembly al pacchetto. Per ulteriori informazioni, vedere

- [web.config file Impostazioni modifica](/previous-versions/office/developer/sharepoint-2007/bb802890(v=office.12)) e registrazione di un [assembly di web part come Cassaforte controllo](/previous-versions/office/developer/sharepoint2003/dd587360(v=office.11)).

> [!IMPORTANT]
> Queste procedure sono a scopo illustrativo. Contrassegnare i controlli come sicuri solo se si è certi che siano sicuri.

## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>Contrassegno Cassaforte controlli nella proprietà Cassaforte Entries del controllo

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>Per contrassegnare i controlli come sicuri o non sicuri nella proprietà safe control entries

1. Creare una SharePoint con un progetto Web part visuale.

2. Aggiungere due controlli alla web part: una casella di testo e un pulsante. Lasciare i valori predefiniti, textBox1 e Button1, rispettivamente.

3. Aggiungere due voci alla proprietà control **Entries Cassaforte web** part. A tale scopo, scegliere il pulsante con i puntini di sospensione ( ASP.NET ![Mobile Designer](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")) accanto alla proprietà Cassaforte **Control Entries** nella **finestra** Proprietà.

     Verrà **Cassaforte la finestra di dialogo** Voci di controllo di configurazione .

4. Nella finestra **Cassaforte voci** di controllo di  sicurezza scegliere due volte il pulsante  Aggiungi per aggiungere due voci di controllo sicuro al riquadro Membri: una per il pulsante e una per la casella di testo.

5. Scegliere la prima voce di controllo sicuro e quindi modificare il valore della relativa proprietà **Cassaforte in** **False**, la relativa proprietà **Nome** tipo su **Button1** e la relativa proprietà **Cassaforte Against Script** su **False**.

     Questo passaggio identifica il controllo pulsante come controllo non sicuro.

6. Scegliere la seconda voce di controllo sicura nell'elenco. Lasciare il valore della relativa **proprietà Cassaforte** su **True** e impostarne la proprietà **Type Name** su **TextBox1** e la relativa proprietà Cassaforte **Against Script** su **True.**

     Il controllo casella di testo è ora contrassegnato come controllo sicuro contro l'inserimento di script.

7. Scegliere il pulsante **OK** per chiudere la finestra di dialogo.

## <a name="marking-safe-controls-in-the-package-designer"></a>Contrassegno Cassaforte controlli in Progettazione pacchetti

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>Per contrassegnare i controlli come sicuri o non sicuri in Progettazione pacchetti

1. Creare una SharePoint con un progetto Web part visuale.

2. Aggiungere due controlli alla web part: una casella di testo e un pulsante. Lasciare i valori predefiniti, textBox1 e Button1, rispettivamente.

     Prendere nota dello spazio dei nomi del controllo perché verrà usato in un secondo momento.

3. Nella barra dei menu scegliere **Compila**  >  **compila soluzione** per compilare il progetto.

4. Creare un'SharePoint soluzione.

5. In **Esplora soluzioni** aprire il menu di scelta rapida per il file *Package.Package* e quindi scegliere Apri **per** aprire **Progettazione pacchetti.**

6. In **Progettazione pacchetti** scegliere la **scheda** Avanzate.

7. In **Assembly aggiuntivi** scegliere il pulsante **Aggiungi** e quindi scegliere Aggiungi **assembly esistente** dall'elenco.

8. Nella finestra **di dialogo Aggiungi assembly** esistente scegliere i puntini di sospensione ( ASP.NET ![puntini](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")di sospensione di Mobile Designer ) accanto a **Percorso origine**.

9. Scegliere l'assembly SharePoint soluzione creata nel passaggio 1 e quindi scegliere il **pulsante** Apri.

10. Per questo esempio, lasciare **l'opzione Destinazione** distribuzione impostata su GlobalAssemblyCache.

     Questo passaggio determina la distribuzione dell'assembly nella Global Assembly Cache (GAC) di sistema. Se si vuole distribuire l'assembly nella cartella Applicazione Web (Bin), selezionare invece tale opzione. Per altre informazioni, vedere [Distribuzione di Web part in SharePoint Foundation.](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14))

11. Nella casella **Cassaforte controlli** personalizzati scegliere il pulsante Click here to add a new item (Fare clic qui per aggiungere **un nuovo** elemento).

12. Immettere i valori per le proprietà della tabella seguente.

    |Nome della proprietà|Valore|
    |-------------------|-----------|
    |Spazio dei nomi|Spazio dei nomi completo per il controllo, ad esempio **BdcModelProject1.VisualWebPart1.**|
    |Nome tipo|Button1|
    |Nome assembly|Un nome di assembly sicuro, ad esempio Microsoft. Office. SharePoint. ClientExtensions, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c.|
    |Safe|Deselezionare **la Cassaforte** di controllo.|
    |Cassaforte In base allo script|Lasciare **deselezionata Cassaforte la casella di controllo** In base allo script.|

    > [!NOTE]
    > Il **valore Nome** assembly per  gli assembly  aggiunti tramite la scheda Avanzate di Progettazione pacchetti non può essere un token, ma deve essere un assembly con nome sicuro. Per altre informazioni, vedere [Creazione e utilizzo degli assembly con nome sicuro](/previous-versions/dotnet/netframework-4.0/xwb8f617(v=vs.100)).

13. Premere **TAB per** creare un'altra voce di controllo sicuro.

14. Scegliere di **nuovo il pulsante Fare clic qui per aggiungere un** nuovo elemento.

15. Immettere i valori per le proprietà della tabella seguente.

    |Nome della proprietà|Valore|
    |-------------------|-----------|
    |Spazio dei nomi|Spazio dei nomi completo per il controllo, ad esempio **BdcModelProject1.VisualWebPart1.**|
    |Nome tipo|TextBox1|
    |Nome assembly|Un nome di assembly sicuro, ad esempio Microsoft. Office. SharePoint. ClientExtensions, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c.|
    |Safe|Selezionare la **Cassaforte** di controllo.|
    |Cassaforte In base allo script|Selezionare la casella Cassaforte against script (Da **script).**|

16. Premere **TAB** e quindi fare clic sul **pulsante OK** per chiudere la finestra di dialogo.

## <a name="see-also"></a>Vedi anche
- [Fornire informazioni sulla creazione di pacchetti e sulla distribuzione negli elementi del progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Creare pacchetti e distribuire SharePoint soluzioni](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
