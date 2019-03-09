---
author: pkrebs
ms.author: pkrebs
title: Aggiornamento di apprendimento personalizzato
ms.date: 02/10/2019
description: Installazione di Web part manuale per l'apprendimento personalizzato per Office 365
ms.openlocfilehash: f9729c922b374cc6b775737fa7c7c76a4719534c
ms.sourcegitcommit: b6617bbbaee0784d6216e96052c2469f97cf51e9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2019
ms.locfileid: "30411896"
---
# <a name="manual-upgrade-for-custom-learning"></a>Aggiornamento manuale per l'apprendimento personalizzato

L'apprendimento personalizzato per Office 365 fornisce un processo di aggiornamento manuale per le organizzazioni che hanno partecipato a piloti precedenti. Con il processo di aggiornamento, le organizzazioni possono continuare a utilizzare il proprio sito di apprendimento personalizzato corrente aggiungendo la nuova Web part di apprendimento personalizzato avanzata al catalogo delle app di SharePoint e quindi eseguendo uno script di PowerShell. Di seguito viene fornita una panoramica del processo di aggiornamento: 

- Verificare che la persona responsabile del caricamento della nuova Web part e dell'esecuzione dello script PowerShell disponga delle autorizzazioni necessarie
- Caricare la Web part, il file customlearning. sppkg, nel catalogo app Office 365 tenant
- Eseguire uno script di PowerShell che configurerà il tenant con gli elementi necessari per l'apprendimento personalizzato
- Passare alla pagina CustomLearningAdmin. aspx nel sito di apprendimento personalizzato per inizializzare la configurazione personalizzata di Ccontent.

## <a name="prerequisites"></a>Prerequisiti
Per garantire un aggiornamento corretto dell'apprendimento personalizzato, è necessario che vengano soddisfatti i prerequisiti seguenti. 

- È necessario aver configurato un catalogo app a livello di tenant. Se non si dispone di un catalogo app tenant, vedere [configurare il tenant di Office 365](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/set-up-your-developer-tenant#create-app-catalog-site) e seguire la sezione Crea sito Catalogo app. 
- Se è già stato effettuato il provisioning del catalogo app a livello di tenant, è necessario accedere a un account che disponga dei diritti di caricamento di un pacchetto. Si tratta in genere di un account con il ruolo di amministratore di SharePoint. 
- Se un account con il ruolo di amministratore di SharePoint non funziona: passare all'interfaccia di amministrazione di SharePoint, selezionare il catalogo app, fare clic su proprietari e accedere come uno degli amministratori della raccolta siti o aggiungere l'account amministratore di SharePoint che non è riuscito al sito Elenco degli amministratori delle raccolte. 

## <a name="step-1---get-the-web-part-package-and-setup-script-from-github"></a>Passaggio 1-ottenere il pacchetto Web part e lo script di installazione da GitHub
Come parte del processo di installazione, è necessario il pacchetto Web part di apprendimento personalizzato e lo script di installazione di PowerShell.

1. Andare al [repository di apprendimento GitHub personalizzato](https://github.com/pnp/custom-learning-office-365).
2. Fare clic su **Clone o download**e quindi **scaricare zip**.   
3. Salvare il file **zip** in una posizione nell'unità locale.
4. Estrarre il file **zip** nell'unità locale.

## <a name="step-2---upload-the-web-part-to-the-tenant-app-catalog"></a>Passaggio 2: caricare la Web part nel catalogo app tenant
Per configurare l'apprendimento personalizzato per Office 365, caricare il file customlearning. sppkg nel catalogo app a livello di tenant e distribuirlo. Per informazioni dettagliate su come aggiungere un'app al catalogo app, vedere [utilizzare il catalogo app per rendere disponibili le app aziendali personalizzate per l'ambiente di SharePoint Online](https://docs.microsoft.com/en-us/sharepoint/use-app-catalog) .

1. In Office 365, fare clic su **amministratore**.
2. In interfaccia di **Amministrazione**, fare clic su **SharePoint**.
3. Fare clic su **Apps** > **App Catalog** > **distribuire le app per SharePoint.**
4. Fare clic su **carica** > **scegliere file**.
5. Nella cartella in cui è stato salvato il file ZIP, selezionare la cartella **WebPart** , quindi selezionare **customlearning. sppkg.**
6. Fare clic su **Distribuisci**.

## <a name="step-5--execute-powershell-configuration-script"></a>Passaggio 5-esecuzione dello script di configurazione di PowerShell
Uno script `CustomLearningConfiguration.ps1` di PowerShell è incluso nel download zip da GitHub. È necessario eseguire lo script per creare tre [Proprietà tenant](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/tenant-properties) utilizzate dalla soluzione. Lo script consente inoltre di creare due [pagine dell'applicazione di una singola parte](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/single-part-app-pages) nella raccolta pagine del sito per ospitare l'amministratore e le web part dell'utente in una posizione nota. Queste pagine dell'app sono:

- CustomAdministration. aspx
- CustomViewer. aspx

### <a name="to-run-the-powershell-script"></a>Per eseguire lo script di PowerShell
- Tramite PowerShell, eseguire lo `CustomLearningConfiguration.ps1` script che si trova nella cartella WebPart dalla zip github. In caso di esito positivo, verranno visualizzate tre coppie chiave/valore e l' **amministratore di apprendimento personalizzato per disattivare...** nella finestra di comando.

### <a name="disabling-telemetry-collection"></a>Disabilitazione della raccolta di telemetria
L'apprendimento personalizzato include la verifica della telemetria di anonimi opt-in, che per impostazione predefinita è impostata su attivato. Se si desidera disattivare la verifica della telemetria, modificare lo `CustomlearningConfiguration.ps1` script per impostare la `$optInTelemetry` variabile su. `$false`

## <a name="step-6---initialize-web-part-custom-configuration"></a>Passaggio 6-inizializzare la configurazione personalizzata della web part
Dopo che lo script di PowerShell è stato eseguito correttamente `<YOUR-SITE-COLLECTION-URL>/SitePages/CustomLearningAdmin.aspx`, accedere a. L'apertura di **CustomLearningAdmin. aspx** consente di inizializzare l'elemento di elenco **CustomConfig** che configura l'apprendimento personalizzato per il primo utilizzo. Dovrebbe essere visualizzata una pagina simile alla seguente:

![CG-adminapppage. png](media/cg-adminapppage.png)

## <a name="add-owners-to-site"></a>Aggiungere proprietari al sito
Come amministratore del tenant, è improbabile che tu sia la persona che Personalizza il sito, quindi dovrai assegnare alcuni proprietari al sito. I proprietari dispongono di privilegi amministrativi per il sito in modo che possano modificare le pagine del sito e rimarcare il sito. Sono inoltre in grado di nascondere e visualizzare i contenuti forniti tramite la Web part di apprendimento personalizzata. Avranno anche la possibilità di creare playlist personalizzate e assegnarle a sottocategorie personalizzate.  

1. Scegliere **autorizzazioni sito**dal menu **Impostazioni** di SharePoint.
2. Fare clic su **Impostazioni avanzate di autorizzazione**.
3. Fare clic su **apprendimento personalizzato per i proprietari di Office 365**.
4. Fare clic su **nuovo** > **Aggiungi utenti a questo gruppo**, aggiungere le persone che si desidera siano proprietari e quindi fare clic su **Condividi**.

L'aggiornamento è stato completato. Per ulteriori informazioni su come personalizzare il sito di apprendimento personalizzato e la Web part per l'ambiente in uso, vedere [Customize the Training Experience](custom_overview.md).

## <a name="upgrade-instructions-for-site-owners"></a>Istruzioni di aggiornamento per i proprietari di siti
L'apprendimento personalizzato per Office 365 ha introdotto una serie di miglioramenti per la Web part. L'utilizzo della web part è dettagliatamente incluso nella sezione [Customize Learning Experience](custom_overview.md) . Per il momento, il proprietario del sito deve:  

- Verificare che la Web part apprendimento personalizzato per Office 365 sia disponibile. 
- Sostituire la Web part esistente nelle pagine con la nuova Web part
- Sostituisci tutti i collegamenti che puntano alla web part precedente

### <a name="verify-the-custom-learning-for-office-365-web-part-is-available"></a>Verificare che la Web part apprendimento personalizzato per Office 365 sia disponibile
1.  Dal sito di apprendimento personalizzato, fare clic su **Impostazioni**, quindi fare clic su ***Aggiungi una pagina**.
2.  Fare clic **+** sull'icona nella pagina per aggiungere una Web part e quindi selezionare la Web part **apprendimento personalizzato per Office 365** . La pagina dovrebbe essere simile all'immagine seguente:

[CG-adminapppage. png](media/cg-adminapppage.png)
 
### <a name="replace-the-old-web-part-with-the-new-web-part"></a>Sostituire la Web part precedente con la nuova Web part
Prima di sostituire la Web part di apprendimento personalizzato o di apportare modifiche al sito, è consigliabile leggere la documentazione [Personalizza l'esperienza di apprendimento](custom_overview.md) , in quanto spiega come utilizzare la nuova Web part. 

Per aggiornare il sito di apprendimento personalizzato, sostituire le istanze esistenti della web part con la nuova Web part. Anche se non è possibile verificare la posizione in cui è stata aggiunta la Web part, le indicazioni per i precedenti piloti sono state aggiunte alla web part nelle pagine seguenti, quindi cerca di sostituire la Web part in queste pagine:

- Get-started-with-Office-365. aspx
- Get-started-with-Microsoft-Teams. aspx
- Get-started-with-OneDrive. aspx
- Get-started-with-SharePoint. aspx

### <a name="replace-existing-links-to-the-web-part"></a>Sostituisci collegamenti esistenti alla web part
Con i miglioramenti apportati alla nuova Web part, il collegamento a una playlist è stato modificato. Come parte dell'aggiornamento, è necessario sostituire qualsiasi collegamento alla web part, incluse le voci di menu e i collegamenti nella Home page. Prima di sostituire la Web part di apprendimento personalizzato o di apportare modifiche al sito, è consigliabile leggere la documentazione [Personalizza l'esperienza di apprendimento](custom_overview.md) , in quanto spiega come utilizzare la nuova Web part. 

## <a name="recreate-existing-playlists"></a>Ricreare playlist esistenti 
Per garantire il corretto funzionamento delle playlist, è necessario ricreare tutte le playlist create con la versione precedente della web part. Prima di eliminare le playlist, creare un elenco di elenchi di riproduzione personalizzati e risorse associate in modo da poterli ricreare facilmente tramite la nuova Web part di apprendimento personalizzato. Creare una copia di una playlist e quindi eliminarla. È possibile utilizzare il campo JSONData per creare una copia del contenuto di una playlist prima di eliminarla. In questo modo sarà più facile creare in un secondo momento.


• Dal sito di apprendimento personalizzato, fare clic su impostazioni > contenuto del sito. • Selezionare una playlist, selezionare i puntini di ellisse, selezionare modifica, quindi copiare il contenuto del campo JSONData e salvarlo in blocco note o in un documento separato per riferimenti successivi. Selezionare Annulla.
• Selezionare la playlist, selezionare i puntini di ellisse e quindi scegliere Elimina.
• È ora possibile ricreare la playlist con la nuova Web part.
Per istruzioni sull'utilizzo della nuova Web part apprendimento personalizzato per Office 365, vedere https://docs.microsoft.com/en-us/office365/customlearning/custom_overview.

## <a name="step-8---chan"></a>Passaggio 8-Chan

### <a name="next-steps"></a>Operazioni successive
- [Personalizzare](custom_overview.md) l'esperienza di formazione per l'organizzazione.
