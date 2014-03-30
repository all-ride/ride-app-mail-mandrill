## Configuration

Set the following configuration to _parameters.json_ in your _config_ directory:

    mail.mandrill.apikey = "your-api-key"

### Sending Mails Using Mandrill

    <?php

    use ride\library\mail\transport\MandrillTransport;

    function foo(MandrillTransport $mandrillTransport) {
        // create a message
        $message = $mandrillTransport->createMessage();
        $message->setFrom('me@domain.com');
        $message->setTo('recipient@domain.com');
        $message->setSubject('subject');
        $message->setMessage('Your message');

        // mandrill extension
        $message->addTag('your-tag');
        $message->setSubaccount('subaccount-id');

        // send it
        $mandrillTransport->send($message);
    }
