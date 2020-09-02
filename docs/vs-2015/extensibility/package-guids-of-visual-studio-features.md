---
title: GUID del pacchetto delle funzionalità di Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C package GUIDs
ms.assetid: f56f0356-f3ac-48bc-9674-94259e29a4df
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8601b4f072c206ab19fdcb4a7248e79784af934a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62546811"
---
# <a name="package-guids-of-visual-studio-features"></a>GUID di pacchetto delle funzionalità di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile usare i seguenti GUID nel file con estensione pkgundef dell'applicazione shell isolata per escludere pacchetti specifici dall'applicazione.

## <a name="package-guids"></a>GUID del pacchetto

|Area di funzionalità|Nome pacchetto non elaborato|GUID pacchetto|
|------------------|----------------------|------------------|
|IDE di base|Annulla pacchetto|{1D76B2E0-F11B-11D2-AFC3-00105A9991EF}|
||Pacchetto dell'ambiente di Visual Studio|{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}|
||Pacchetto di definizione comandi di Visual Studio|{44E07B02-29A5-11D3-B882-00C04F79F802}|
||Elenco di elenchi di directory di Visual Studio|{5010C52F-44AB-4051-8CE1-D36C20D989B4}|
||Pacchetto IDE comune di Visual Studio|{6E87CFAD-6C05-4ADF-9CD7-3B7943875B7C}|
||Pacchetto di menu ambiente Visual Studio|{715F10EB-9E99-11D2-BFC2-00C04F990235}|
||Pacchetto di gestione librerie COM+ di Visual Studio|{ED8979BC-B02F-4dA9-A667-D3256C36220A}|
||Pacchetto di integrazione del controllo del codice sorgente di Visual Studio|{53544C4D-E3F8-4AA0-8195-8A8D16019423}|
||Pacchetto di compilazione della soluzione Visual Studio|{282BD676-8B5B-11D0-8A34-00A0C91E2ACD}|
||Pacchetto di gestione del testo|F5E7E720-1401-11D1-883B-0000F87579D2|
||Pacchetto VsSettings di Visual Studio|{F74C5077-D848-4630-80C9-B00E68A1CA0C}|
|Guida|Pacchetto della Guida di Visual Studio|{4A791146-19E4-11D3-B86B-00C04F79F802}|
|Elenco attività, Elenco errori|ErrorListPackage|{4A9B7E50-AA16-11D0-A8C5-00A0C921A4D2}|
|Struttura della classe|Pacchetto struttura classi|{21AF45B0-FFA5-11D0-G63F-00A0C922E851}|
|Programma di installazione controlli della casella degli strumenti|Pacchetto di installazione controlli della casella degli strumenti|{2C298B35-07DA-45F1-96A3-BE55D91C8d7A}|
|Progetti Web|Microsoft. VisualStudio. Web|{349C5850-65DF-11DA-9384-00065B846F21}|
||Pacchetto del sistema di progetto Visual Web Developer|{39C9C826-8EF8-4079-8C95-428F5B1C323F}|
||Pacchetto di persistenza progetto Visual Web Developer|{8FF02D1A-C177-4AC8-A62F-88FC6EA65F57}|
||Pacchetto di migrazione Web di Visual Web Developer|{C1DAB116-2D63-493A-B970-10D7DD0B476E}|
||Pacchetto Web Visual Web Developer|{E7f851C8-6267-4794-B0FE-7BCAB6DACBB4}|
||Web di Visual Web Developer|{DC7F691A-91FC-4F7B-923E-FE829C3A18DC}|
|Editor HTML|Pacchetto di editor di Visual Studio HTM|{1B437D20-F8FE-11D2-A6AE-00104BCC7269}|
||Pacchetto Editor origine HTML Visual Web Developer|{BFCC0C3C-6F87-4285-A6C8-BB616061800D}|
|CSS (editor)|Pacchetto di modifica CSS di Visual Studio|{A764E895-518D-11d2-9A89-00C04F79EFC3}|
|Editor XML|Pacchetto dell'editor XML di Visual Studio|{87569308-4813-40A0-9CD0-D7A30838CA3F}|
|Web browser|Pacchetto del browser Web di Visual Studio|{E8B06F41-6D01-11D2-AA7D-00C04F990343}|
||Factory del progetto di applicazione Web, per la visualizzazione nella funzionalità del browser|{349C5851-65DF-11DA-9384-00065B846F21}|
|Editor binario|Pacchetto editor binario di Visual Studio|{5B98C2C0-CD7B-11D0-92DF-00A0C9138C45}|
|Progettazione Windows Form|Progettazione Windows Form pacchetto di hosting|{68939055-38E0-4D17-92CB-8909710D8178}|
||Pacchetto di Progettazione Windows Form|{7494682B-37A0-11D2-A273-00C04F8EF4FF}|
||Pacchetto di risorse Progettazione Windows Form|{7B5D447B-0B12-41EA-A84E-C822034422D4}|
||Pacchetto di configurazione dell'applicazione Windows Forms|{80C7728B-70A6-4528-8669-73E02D1B9C41}|
||Pacchetto della finestra di progettazione ElementHost|{7EAB3C71-59FF-4571-A5F3-643F255FC2E6}|
|Interfaccia utente del debugger|Debugger di Visual Studio|{C9DD4A57-47FB-11D2-83E7-00C04F9902C1}|
|Strumenti di database|Pacchetto di Visual Database Tools|{220A4C17-7E7C-4663-BBCC-5E607C6543CD}|
||Strumenti di progettazione di Visual Studio Database Tools|{EF828E39-70F5-4b8e-A3A0-4C0ECD28A69A}|
||Finestre di progettazione dati di Visual Studio|{D6C919AA-1217-41E2-a13B-9B92E1866305}|
||Pacchetto di dati di Visual Studio|{E1AA7737-69BE-43d0-A425-E3097651E192}|
||Pacchetto di estendibilità di progettazione dati di Visual Studio|{A8F602E2-40CE-4dAF-AE82-A457A91728B9}|
||Pacchetto di Esplora risorse e finestre di progettazione di Visual Studio|{8D8529D3-625D-4496-8354-3DAD630ECC1B}|
||Progettazione report Microsoft|{F3A96850-E2AE-4E00-9278-8FE23F225A0D}|
|Runtime DSL|CommonModelingPackage|{D1091694-EA72-4BDD-8918-78324CC25448}|
||Microsoft. VisualStudio. TextTemplating|{A9696DE6-E209-414D-BBEC-A0506fb0E924}|
|Supporto per SourceSafe|Pacchetto del provider di Visual SourceSafe|{AA8EB8CD-7A51-11D0-92C3-00A0C9138C45}|
||Pacchetto stub del provider di Visual SourceSafe|{53544C4D-B03D-4209-A7D0-D9DD13A4019B}|
|WPF Designer|WPFFlavor.WPFPackage|{B3BAE735-386C-4030-8329-EF48EEDA4036}|
||XamlDesignerPackage|{512be089-83ec-4cc6-8483-cf16565ae209}|
||XamlLanguagePackage|{2ef1ec52-c8bf-4fe0-8ece-ba9c0d5d1603}|
||XamlDiagnosticsPackage|{8291c340-36b8-4c91-8c40-cce75398ff75}|
|Frammenti di codice|Pacchetto di frammenti di Visual Studio Code|{0B680757-2C29-4531-80FA-535A5178AA98}|
|Supporto del progetto di linguaggio gestito|Enumeratore componente di Visual Studio|{588205E0-66e0-11D3-8600-00C04F6123B3}|
||Pacchetto di impostazioni e progettazione progetti di Visual Studio|{67909B06-91E9-4F3E-AB50-495046BE9A9A}|
|Esporta modello…|Esporta pacchetto modello|{F1E4CFCA-4573-4345-8718-7BDE2b1F0BE8}|

 Alcuni pacchetti non devono mai essere rimossi perché molte altre funzionalità sono dipendenti da tali pacchetti. Ad esempio, quelli elencati in "IDE di base" non devono mai essere rimossi.

 Alcune funzionalità non possono essere rimosse completamente. Non è ad esempio possibile annullare la registrazione di un pacchetto per rimuovere **Visualizzazione classi** e i menu, le opzioni e i servizi associati. La finestra **Visualizzazione classi** viene fornita dal pacchetto dell'ambiente di Visual Studio, che fornisce anche altre funzionalità chiave dell'IDE. Se si desidera rimuovere **Visualizzazione classi**, è **necessario rimuovere anche**le pagine **Opzioni** ambiente, **finestra di comando**e finestra di **output** .
