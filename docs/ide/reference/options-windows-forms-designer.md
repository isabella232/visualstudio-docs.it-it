---
title: Opzioni, Progettazione Windows Form, Generale
ms.date: 08/09/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.WindowsFormsDesigner.General
helpviewer_keywords:
- Windows Forms Designer options
- Options dialog box, Windows Forms Designer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 2a72b27dc2277501d0e0957c8b89b551f4d6852d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568061"
---
# <a name="options-dialog-box-windows-forms-designer"></a>Finestra di dialogo Opzioni: Progettazione Windows Form

La pagina delle opzioni di Progettazione Windows Form consente di impostare le preferenze per le griglie e altre funzionalità di Progettazione Windows Form in Visual Studio. Aprire la finestra di dialogo **Opzioni** dal menu **Strumenti**.

## <a name="code-generation-settings"></a>Impostazioni di generazione del codice

**Generazione di codice ottimizzata**\
Abilita la generazione del codice ottimizzata. Alcuni controlli potrebbero non essere compatibili con questa modalità. Per rendere effettive le modifiche, è necessario chiudere e riaprire Visual Studio.

## <a name="high-dpi-support"></a>Supporto per valori DPI alti

**Notifiche di ridimensionamento DPI**\
Mostra un messaggio in Progettazione Windows Form che può riavviare Visual Studio con un ridimensionamento del 100%. Per altre informazioni, vedere [Disabilitare la compatibilità con DPI in Visual Studio](/dotnet/framework/winforms/disable-dpi-awareness-visual-studio).

## <a name="layout-settings"></a>Impostazioni layout

**Dimensione cella griglia predefinita**\
Imposta la spaziatura, in pixel, tra le linee della griglia orizzontale e verticale nella finestra di progettazione. Le dimensioni predefiniti sono 8, 8. Le dimensioni massime sono 200, 200.

**Modalità layout**\
Specifica il sistema di allineamento da usare per il layout. È possibile scegliere SnapToGrid o le guide di allineamento.

**Mostra griglia**\
Specifica se le finestre di progettazione visualizzano la griglia di ridimensionamento. Per impostazione predefinita, la griglia è attivata.

**Aggancia alla griglia**\
Determina se le finestre di progettazione bloccano oggetti e controlli sulla griglia. In altre parole, il ridimensionamento e lo spostamento degli elementi nella finestra di progettazione sono vincolati all'incremento di GridSize quando questa funzionalità è attivata. L'attivazione di SnapToGrid facilita l'allineamento preciso dei vari aspetti dell'interfaccia utente, ma limita la libertà con cui si possono posizionare i controlli. Per impostazione predefinita, SnapToGrid è attivato.

## <a name="object-bound-smart-tag-settings"></a>Impostazioni smart tag associati a oggetti

**Apri automaticamente smart tag**\
Determina se i controlli e i componenti visualizzano gli smart tag. Non tutti i controlli e i componenti supportano gli smart tag.

## <a name="refactoring"></a>Refactoring

**Abilitare il refactoring al ridenominazioneEnable Refactoring on Rename**\
Quando è impostato su `true`, viene eseguita un'operazione di refactoring di ridenominazione quando si rinomina un componente dalla finestra Proprietà o Struttura documento.

## <a name="toolbox"></a>Casella degli strumenti

**Popola automaticamente la casella degli strumenti**\
Determina se la finestra casella degli strumenti viene popolata automaticamente con i componenti e i controlli compilati dal progetto.
