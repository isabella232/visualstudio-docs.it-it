---
title: GUID della funzionalità di Visual Studio creare un pacchetto | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C package GUIDs
ms.assetid: f56f0356-f3ac-48bc-9674-94259e29a4df
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e23d1fdde0e7080e2226e02a38213ccb3f2640a9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733386"
---
# <a name="package-guids-of-visual-studio-features"></a>GUID di pacchetto di funzionalità di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile utilizzare il seguente GUID nel file con estensione pkgundef dell'applicazione shell isolata da escludere pacchetti specifici dell'applicazione.  
  
## <a name="package-guids"></a>GUID di pacchetto  
  
|Area funzionalità|Nome del pacchetto non elaborati|GUID pacchetto|  
|------------------|----------------------|------------------|  
|Core dell'IDE|Annulla pacchetto|{1D76B2E0-F11B-11D2-AFC3-00105A9991EF}|  
||Pacchetto dell'ambiente Visual Studio|{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}|  
||Pacchetto di definizione di comandi di Visual Studio|{44E07B02-29A5-11D3-B882-00C04F79F802}|  
||Pacchetto di elenco Directory di Visual Studio|{5010C52F-44AB-4051-8CE1-D36C20D989B4}|  
||Pacchetto dell'IDE più comune di Visual Studio|{6E87CFAD-6C05-4ADF-9CD7-3B7943875B7C}|  
||Pacchetto dal Menu dell'ambiente Visual Studio|{715F10EB-9E99-11D2-BFC2-00C04F990235}|  
||Pacchetto di gestione librerie di Visual Studio COM+|{ED8979BC-B02F-4dA9-A667-D3256C36220A}|  
||Pacchetto integrazione controllo codice sorgente di Visual Studio|{53544C4D-E3F8-4AA0-8195-8A8D16019423}|  
||Pacchetto di compilazione di soluzioni di Visual Studio|{282BD676-8B5B-11D0-8A34-00A0C91E2ACD}|  
||Pacchetto di gestione di testo|{F5E7E720-1401-11d1-883B-0000F87579D2}|  
||Pacchetto di Visual Studio VsSettings|{F74C5077-D848-4630-80C9-B00E68A1CA0C}|  
|?|Pacchetto di supporto di Visual Studio|{4A791146-19E4-11D3-B86B-00C04F79F802}|  
|Elenco di attività, elenco errori|ErrorListPackage|{4A9B7E50-AA16-11D0-A8C5-00A0C921A4D2}|  
|Struttura di classe|Pacchetto di struttura di classe|{0: G63F-00A0C922E851 21AF45B0 FFA5 - 11D}|  
|Programma di installazione di controlli della casella degli strumenti|Pacchetto di installazione di controlli della casella degli strumenti|{2C298B35-07DA-45F1-96A3-BE55D91C8d7A}|  
|Progetti Web|Microsoft.VisualStudio.Web|{349C5850-65DF-11DA-9384-00065B846F21}|  
||Pacchetto del sistema del progetto Visual Web Developer|{39C9C826-8EF8-4079-8C95-428F5B1C323F}|  
||Pacchetto della persistenza del progetto Visual Web Developer|{8FF02D1A-C177-4AC8-A62F-88FC6EA65F57}|  
||Pacchetto di Visual Web Developer Web migrazione|{C1DAB116-2D63-493A-B970-10D7DD0B476E}|  
||Pacchetto di Web di Visual Web Developer|{E7f851C8-6267-4794-B0FE-7BCAB6DACBB4}|  
||Web di Visual Web Developer|{DC7F691A-91FC-4F7B-923E-FE829C3A18DC}|  
|Editor HTML|Package Editor di Visual Studio HTM|{1B437D20-F8FE-11D2-A6AE-00104BCC7269}|  
||Editor origine HTML di Visual Web Developer pacchetto|{BFCC0C3C-6F87-4285-A6C8-BB616061800D}|  
|CSS (editor)|Pacchetto modifica CSS di Visual Studio|{A764E895-518D-11d2-9A89-00C04F79EFC3}|  
|Editor XML|Package Editor XML di Visual Studio|{87569308-4813-40A0-9CD0-D7A30838CA3F}|  
|Web browser|Pacchetto di Visual Studio Web Browser|{E8B06F41-6D01-11D2-AA7D-00C04F990343}|  
||Factory del progetto dell'applicazione Web, per la visualizzazione in funzionalità del Browser|{349C5851-65DF-11DA-9384-00065B846F21}|  
|Editor binario|Package Editor binario di Visual Studio|{5B98C2C0-CD7B-11D0-92DF-00A0C9138C45}|  
|Progettazione Windows Form|Pacchetto di Hosting della finestra di progettazione di Windows Form|{68939055-38E0-4D17-92CB-8909710D8178}|  
||Pacchetto della finestra di progettazione di Windows Form|{7494682B-37A0-11D2-A273-00C04F8EF4FF}|  
||Pacchetto di risorse della finestra di progettazione Windows Form|{7B5D447B-0B12-41EA-A84E-C822034422D4}|  
||Pacchetto di configurazione dell'applicazione Windows Form|{80C7728B-70A6-4528-8669-73E02D1B9C41}|  
||Pacchetto di progettazione ElementHost|{7EAB3C71-59FF-4571-A5F3-643F255FC2E6}|  
|Interfaccia utente del debugger|Debugger di Visual Studio|{C9DD4A57-47FB-11D2-83E7-00C04F9902C1}|  
|Strumenti di database|Pacchetto di Visual Database Tools|{220A4C17-7E7C-4663-BBCC-5E607C6543CD}|  
||Finestre di progettazione di Visual Studio Database Tools|{EF828E39-70F5-4b8e-A3A0-4C0ECD28A69A}|  
||Finestre di progettazione di Visual Studio Data|{D6C919AA-1217-41E2-a13B-9B92E1866305}|  
||Pacchetto di dati di Visual Studio|{E1AA7737-69BE-43d0-A425-E3097651E192}|  
||Pacchetto di estensibilità di progettazione di Visual Studio Data|{A8F602E2-40CE-4dAF-AE82-A457A91728B9}|  
||Pacchetto di finestre di progettazione e finestre di esplorazione di Visual Studio|{8D8529D3-625D-4496-8354-3DAD630ECC1B}|  
||Progettazione Report di Microsoft|{F3A96850-E2AE-4E00-9278-8FE23F225A0D}|  
|Runtime di linguaggio specifico di dominio|CommonModelingPackage|{D1091694-EA72-4BDD-8918-78324CC25448}|  
||Microsoft.VisualStudio.TextTemplating|{A9696DE6-E209-414D-BBEC-A0506fb0E924}|  
|Supporto di SourceSafe|Pacchetto di Visual SourceSafe Provider|{AA8EB8CD-7A51-11D0-92C3-00A0C9138C45}|  
||Package Stub Visual SourceSafe Provider|{53544C4D-B03D-4209-A7D0-D9DD13A4019B}|  
|WPF Designer|WPFFlavor.WPFPackage|{B3BAE735-386C-4030-8329-EF48EEDA4036}|  
||XamlDesignerPackage|{512be089-83ec-4cc6-8483-cf16565ae209}|  
||XamlLanguagePackage|{2ef1ec52-c8bf-4fe0-8ece-ba9c0d5d1603}|  
||XamlDiagnosticsPackage|{8291c340-36b8-4c91-8c40-cce75398ff75}|  
|Frammenti di codice|Pacchetto di frammenti di codice di Visual Studio|{0B680757-2C29-4531-80FA-535A5178AA98}|  
|Supporto di progetto linguaggio gestito|Enumeratore di componenti di Visual Studio|{588205E0-66e0-11D3-8600-00C04F6123B3}|  
||Impostazioni di Visual Studio e progetto finestre di progettazione del pacchetto|{67909B06-91E9-4F3E-AB50-495046BE9A9A}|  
|Esporta modello...|Esporta pacchetto di modelli|{F1E4CFCA-4573-4345-8718-7BDE2b1F0BE8}|  
  
 Alcuni pacchetti non devono mai essere rimosso perché molte altre funzionalità hanno dipendenze su di essi. Ad esempio, quelle elencate in "IDE Core" non devono mai essere rimosso.  
  
 Alcune funzionalità non possono essere rimossa completamente. Ad esempio, non è presente alcun pacchetto che è possibile annullarne la registrazione per rimuovere **Visualizzazione classi** e relativo menu associati, opzioni e i servizi. Il **Visualizzazione classi** finestra viene fornita dall'ambiente di pacchetto di Visual Studio, che offre anche altre funzionalità IDE chiave. Se si desidera rimuovere **Visualizzazione classi**, è anche necessario rimuovere **Trova e sostituisci**, l'ambiente **opzioni** pagine, il **finestra comando**e il **Output** finestra.

