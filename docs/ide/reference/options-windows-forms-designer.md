---
title: Opzioni, Progettazione Windows Form, Generale
ms.date: 08/09/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.WindowsFormsDesigner.General
helpviewer_keywords:
- Windows Forms Designer options
- Options dialog box, Windows Forms Designer
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6166c2f0fcdd8c99c459559a699f7b8704aff647
ms.sourcegitcommit: 6b0503ed8d25454d6e39a8e606910b3fa58cf1d2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2019
ms.locfileid: "68981697"
---
# <a name="options-dialog-box-windows-forms-designer"></a>Finestra di dialogo Opzioni: Progettazione Windows Form

La pagina delle opzioni di Progettazione Windows Form consente di impostare le preferenze per le griglie e altre funzionalità di Progettazione Windows Form in Visual Studio. Aprire la finestra di dialogo **Opzioni** dal menu **Strumenti**.

## <a name="code-generation-settings"></a>Impostazioni di generazione del codice

**Generazione del codice ottimizzata**\
Abilita la generazione del codice ottimizzata. Alcuni controlli potrebbero non essere compatibili con questa modalità. Per rendere effettive le modifiche, è necessario chiudere e riaprire Visual Studio.

## <a name="high-dpi-support"></a>Supporto per valori DPI alti

**Notifiche per ridimensionamento DPI**\
Mostra un messaggio in Progettazione Windows Form che può riavviare Visual Studio con un ridimensionamento del 100%. Per altre informazioni, vedere [Disabilitare la compatibilità con DPI in Visual Studio](/dotnet/framework/winforms/disable-dpi-awareness-visual-studio).

## <a name="layout-settings"></a>Impostazioni layout

**Dimensioni predefinite cella della griglia**\
Imposta la spaziatura, in pixel, tra le linee della griglia orizzontale e verticale nella finestra di progettazione. Le dimensioni predefiniti sono 8, 8. Le dimensioni massime sono 200, 200.

**Modalità layout**\
Specifica il sistema di allineamento da usare per il layout. È possibile scegliere SnapToGrid o le guide di allineamento.

**Mostra griglia**\
Specifica se le finestre di progettazione visualizzano la griglia di ridimensionamento. Per impostazione predefinita, la griglia è attivata.

**Blocca sulla griglia**\
Determina se le finestre di progettazione bloccano oggetti e controlli sulla griglia. In altre parole, il ridimensionamento e lo spostamento degli elementi nella finestra di progettazione sono vincolati all'incremento di GridSize quando questa funzionalità è attivata. L'attivazione di SnapToGrid facilita l'allineamento preciso dei vari aspetti dell'interfaccia utente, ma limita la libertà con cui si possono posizionare i controlli. Per impostazione predefinita, SnapToGrid è attivato.

## <a name="object-bound-smart-tag-settings"></a>Impostazioni smart tag associati a oggetti

**Apri automaticamente smart tag**\
Determina se i controlli e i componenti visualizzano gli smart tag. Non tutti i controlli e i componenti supportano gli smart tag.

## <a name="refactoring"></a>Refactoring

**Abilita refactoring durante la ridenominazione**\
Quando è impostato su `true`, viene eseguita un'operazione di refactoring di ridenominazione quando si rinomina un componente dalla finestra Proprietà o Struttura documento.

## <a name="toolbox"></a>Casella degli strumenti

**Popola automaticamente casella degli strumenti**\
Determina se la finestra casella degli strumenti viene popolata automaticamente con i componenti e i controlli compilati dal progetto.