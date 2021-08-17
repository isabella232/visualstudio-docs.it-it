---
title: Pagina delle opzioni della finestra di progettazione XAML
description: Informazioni su come usare la pagina Generale nella sezione finestra di progettazione XAML per specificare la formattazione di elementi e attributi nei documenti XAML.
ms.custom: SEO-VS-2020
ms.date: 03/02/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.XAMLDesigner
- VS.ToolsOptionsPages.XAML_Designer.General
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- uwp
ms.openlocfilehash: 01832b96a9505a9883896cc60027e2029d6b3b45
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122048635"
---
# <a name="xaml-designer-options-page"></a>Pagina delle opzioni della finestra di progettazione XAML

Usare la pagina delle opzioni della **finestra di progettazione XAML** per specificare le modalità di formattazione di elementi e attributi nei documenti XAML. Per aprire questa pagina, scegliere **Opzioni** dal menu **Strumenti**. Per accedere alla pagina delle proprietà della **finestra di progettazione XAML**, scegliere il nodo **Finestra di progettazione XAML**. Le impostazioni della finestra di progettazione XAML vengono applicate quando si apre il documento. Quindi, se si apportano modifiche alle impostazioni, è necessario chiudere e riaprire Visual Studio per visualizzare le modifiche.

> [!NOTE]
> È possibile che le finestre di dialogo e i comandi di menu visualizzati varino da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni vedere [Reimpostare le impostazioni](../environment-settings.md#reset-settings).

## <a name="enable-xaml-designer"></a>Abilita finestra di progettazione XAML

Se selezionata, questa impostazione consente di abilitare la finestra di progettazione XAML. La finestra di progettazione XAML offre un'area di lavoro visiva in cui è possibile modificare i documenti XAML. Alcune funzionalità di Visual Studio, ad esempio IntelliSense per le risorse e il data binding, richiedono l'abilitazione della finestra di progettazione XAML.

Le impostazioni seguenti sono valide solo se è abilitata la finestra di progettazione XAML. Se si modifica questa opzione, sarà necessario riavviare Visual Studio affinché l'impostazione abbia effetto.

## <a name="default-document-view"></a>Visualizzazione documento predefinita

Usare questa impostazione per verificare se la visualizzazione Progettazione appare quando vengono caricati documenti XAML.

|Nome|Descrizione|
|-|-|
|**Vista origine**|Specifica se viene visualizzata solo l'origine XAML nella visualizzazione XAML. L'impostazione è utile quando si caricano documenti di grandi dimensioni.|
|**Visualizzazione Progettazione**|Specifica se deve apparire solo una finestra di progettazione XAML visiva nella visualizzazione XAML.|
|**Doppia visualizzazione**|Specifica se sia la finestra di progettazione XAML visiva che l'origine XAML devono apparire l'una accanto all'altra nella visualizzazione XAML (percorso basato sull'impostazione **Orientamento divisione**).|

## <a name="split-orientation"></a>Orientamento divisione

Usare questa impostazione per stabilire come e quando viene visualizzata la finestra di progettazione XAML quando si modifica un documento XAML. Queste impostazioni si applicano solo quando **Visualizzazione documento predefinita** è impostata su **Doppia visualizzazione**.

|Nome|Descrizione|
|-|-|
|**Vertical**|L'origine XAML viene visualizzata sul lato sinistro della visualizzazione XAML e la finestra di progettazione XAML viene visualizzata sull'altro lato.|
|**Ridimensionamento orizzontale**|La finestra di progettazione XAML viene visualizzata nella parte superiore della visualizzazione XAML e l'origine XAML viene visualizzata sotto di essa.|
|**Default**|Il documento XAML usa l'orientamento divisione consigliato per la piattaforma di destinazione dal progetto del documento. Per la maggior parte delle piattaforme equivale a **Orizzontale**.|

## <a name="zoom-by-using"></a>Zoom mediante

Usare questa impostazione per determinare il funzionamento dello zoom quando si modifica un documento XAML.

|Nome|Descrizione|
|-|-|
|**Rotellina del mouse**|Fare zoom avanti nella finestra di progettazione XAML usando lo scorrimento della rotellina del mouse.|
|**CTRL + rotellina del mouse**|Fare zoom avanti finestra di progettazione XAML clic premendo **CTRL** mentre si scorre la rotellina del mouse.|
|**ALT + rotellina del mouse**|Fare zoom avanti finestra di progettazione XAML clic premendo **ALT** mentre si scorre la rotellina del mouse.|

Queste impostazioni determinano il comportamento della finestra di progettazione quando si modifica un documento XAML.

## <a name="default-zoom-setting"></a>Impostazione predefinita dello zoom

Usare questa impostazione per determinare il valore di zoom predefinito per la visualizzazione del documento XAML.

|Nome|Descrizione|
|-|-|
|**Ultimo utilizzo**|Per impostazione predefinita, usa l'ultimo valore di zoom usato per tutti i documenti XAML. Quando un documento XAML viene aperto per la prima volta, userà l'impostazione "Adatta tutto" solo per la prima volta.|
|**Adatta tutto**|Usare questa opzione per impostare il valore di zoom su "Adatta tutto" per la finestra di progettazione XAML. Quando un documento XAML viene chiuso e riaperto, l'ultimo valore impostato verrà mantenuto per la sessione, ma per le diverse sessioni verrà usato "Adatta tutto" per impostazione predefinita.|

Queste impostazioni determinano il comportamento della finestra di progettazione quando si modifica un documento XAML.

|Nome|Descrizione|
|-|-|
|**Assegna automaticamente un nome agli elementi interattivi durante la creazione**|Specifica se viene indicato un nome predefinito per un nuovo elemento interattivo quando se ne aggiunge uno alla finestra di progettazione.|
|**Inserisci automaticamente le proprietà del layout durante la creazione degli elementi**|Specifica se vengono indicate le proprietà del layout per un nuovo elemento quando se ne aggiunge uno alla finestra di progettazione. Le proprietà di layout sono quelle che influenzano il layout di un controllo, ad esempio, Margin e VerticalAlignment. L'esempio XAML seguente mostra come viene creato un controllo Button, con e senza questa opzione selezionata:<br />`<Button Content="Button" HorizontalAlignment="Left" Margin="245,56,0,0" Grid.Row="1" VerticalAlignment="Top" Width="75"/>`<br />`<Button Content="Button" Grid.Row="1"/>`|
|**Usa layout basato su quadranti**|Specifica se il controllo attualmente selezionato deve essere allineato ai bordi più vicini del contenitore padre. Se questa casella di controllo è deselezionata, gli allineamenti dei controlli non cambiano durante un'operazione di spostamento o creazione.|
|**Inserisci automaticamente elementi della casella degli strumenti**|Specifica se i controlli utente e i controlli personalizzati della soluzione corrente vengono visualizzati automaticamente nella casella degli strumenti.|

## <a name="settings-blend-only"></a>Impostazioni (solo Blend)

Usare queste opzioni per determinare le impostazioni quando si modificano i file XAML con Blend.

|Nome|Descrizione|
|-|-|
|**Zoom mediante**|Fare zoom avanti nella finestra di progettazione XAML scorrendo la rotellina del mouse o premendo il tasto **CTRL** o **ALT** mentre si fa scorrere la rotellina del mouse.|
|**Digitare unità**|Specifica se le misurazioni nella finestra di progettazione sono basate su punti o pixel. Poiché le app di Windows universale non supportano i punti, le unità vengono automaticamente convertite in pixel se **Punti** è selezionata.|

## <a name="artboard-blend-only"></a>Tavola da disegno (solo Blend)

Usare queste impostazioni per determinare il comportamento della finestra di progettazione XAML durante la modifica di documenti XAML in Blend.

### <a name="snapping"></a>Snapping

|Nome|Descrizione|
|-|-|
|**Mostra griglia di allineamento**|Quando questa opzione è selezionata, le linee della griglia vengono visualizzate nella finestra di progettazione per consentire l'allineamento dei controlli. I controlli aggiunti alla finestra di progettazione vengono bloccati sulle linee della griglia se l'opzione **Blocca sulla griglia** è selezionata.|
|**Blocca sulla griglia**|Quando i controlli vengono aggiunti o spostati nella finestra di progettazione vengono bloccati sulla griglia.|
|**Spaziatura griglia**|Specifica la spaziatura tra le linee della griglia in pixel o punti (in base all'impostazione **Digitare unità**).|
|**Blocca sulle guide di allineamento**|Specifica se i controlli vengono bloccati sulle guide di allineamento.|
|**Margine predefinito**|Quando l'opzione **Blocca sulle guide di allineamento** è abilitata, specifica la spaziatura tra il controllo e le guide di allineamento in pixel o punti (in base all'impostazione **Digitare unità**).|
|**Spaziatura interna predefinita**|Quando l'opzione **Blocca sulle guide di allineamento** è abilitata, specifica la spaziatura aggiuntiva tra il controllo e le guide di allineamento in pixel o punti (in base all'impostazione **Digitare unità**).|

### <a name="animation"></a>Animazione

Usare questa impostazione per determinare se viene visualizzato un avviso quando vengono abilitate animazioni dipendenti (non accelerate) in Blend.

### <a name="effects"></a>Effetti

Usare queste impostazioni per determinare se viene eseguito il rendering degli effetti quando si modificano i file XAML nella finestra di progettazione XAML usando Blend.

|Nome|Descrizione|
|-|-|
|**Rendering effetti**|Specifica se viene eseguito il rendering degli effetti quando si modificano i file XAML nella finestra di progettazione XAML usando Blend.|
|**Soglia zoom**|Specifica la percentuale di zoom con cui viene eseguito il rendering degli effetti quando la casella di controllo **Rendering effetti** è selezionata. Se si ingrandisce oltre questa impostazione, non viene più eseguito il rendering degli effetti nella finestra di progettazione XAML.|

## <a name="see-also"></a>Vedi anche

- [XAML in WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [Procedura dettagliata: Compilare una prima applicazione desktop WPF](/dotnet/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application)
