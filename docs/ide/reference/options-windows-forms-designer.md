---
title: Opzioni, Progettazione Windows Form, Generale
description: Informazioni su come usare la pagina generale per impostare le preferenze per le griglie e altre funzionalità del Progettazione Windows Form in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 08/09/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.WindowsFormsDesigner.General
helpviewer_keywords:
- Windows Forms Designer options
- Options dialog box, Windows Forms Designer
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: c55d3dae96ff2757c8a9ba1969c378aa2290d716
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932254"
---
# <a name="options-dialog-box-windows-forms-designer"></a>Finestra di dialogo Opzioni: Progettazione Windows Form

La pagina delle opzioni di Progettazione Windows Form consente di impostare le preferenze per le griglie e altre funzionalità di Progettazione Windows Form in Visual Studio. Aprire la finestra di dialogo **Opzioni** dal menu **Strumenti**.

## <a name="code-generation-settings"></a>Impostazioni di generazione del codice

**Generazione di codice ottimizzato**\
Abilita la generazione del codice ottimizzata. Alcuni controlli potrebbero non essere compatibili con questa modalità. Per rendere effettive le modifiche, è necessario chiudere e riaprire Visual Studio.

## <a name="high-dpi-support"></a>Supporto per valori DPI alti

**Notifiche di ridimensionamento DPI**\
Mostra un messaggio in Progettazione Windows Form che può riavviare Visual Studio con un ridimensionamento del 100%. Per altre informazioni, vedere [Disabilitare la compatibilità con DPI in Visual Studio](/dotnet/framework/winforms/disable-dpi-awareness-visual-studio).

## <a name="layout-settings"></a>Impostazioni layout

**Dimensioni predefinite della cella della griglia**\
Imposta la spaziatura, in pixel, tra le linee della griglia orizzontale e verticale nella finestra di progettazione. Le dimensioni predefiniti sono 8, 8. Le dimensioni massime sono 200, 200.

**Modalità layout**\
Specifica il sistema di allineamento da usare per il layout. È possibile scegliere SnapToGrid o le guide di allineamento.

**Mostra griglia**\
Specifica se le finestre di progettazione visualizzano la griglia di ridimensionamento. Per impostazione predefinita, la griglia è attivata.

**Blocca sulla griglia**\
Determina se le finestre di progettazione bloccano oggetti e controlli sulla griglia. In altre parole, il ridimensionamento e lo spostamento degli elementi nella finestra di progettazione sono vincolati all'incremento di GridSize quando questa funzionalità è attivata. L'attivazione di SnapToGrid facilita l'allineamento preciso dei vari aspetti dell'interfaccia utente, ma limita la libertà con cui si possono posizionare i controlli. Per impostazione predefinita, SnapToGrid è attivato.

## <a name="object-bound-smart-tag-settings"></a>Impostazioni smart tag associati a oggetti

**Apri automaticamente Smart Tag**\
Determina se i controlli e i componenti visualizzano gli smart tag. Non tutti i controlli e i componenti supportano gli smart tag.

## <a name="refactoring"></a>Refactoring

**Abilita refactoring durante la ridenominazione**\
Quando è impostato su `true`, viene eseguita un'operazione di refactoring di ridenominazione quando si rinomina un componente dalla finestra Proprietà o Struttura documento.

## <a name="toolbox"></a>Casella degli strumenti

**Popola automaticamente casella degli strumenti**\
Determina se la finestra casella degli strumenti viene popolata automaticamente con i componenti e i controlli compilati dal progetto.
