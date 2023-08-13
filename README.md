# SendWave

Python Script for sending an emails.

You need a `template library` to create an email with `html`.

## Usage

Here is the usage example with mako template:

    from mako.template import Template

    verification_url  = "https://example.com/verification?token=xxxxxx"

    text  = f"Please visit this link to complete the registration: {verification_url}"
    html  = Template(your_template).render(
        link = verification_url
    )

and here for send the email:

    import sendwave

    sendwave.smtp({
        "login"     : {
            "email"     : "your_email@mail.com",
            "password"  : "your_password"
        },
        "server"    : {
            "host"      : 'smtp.mail.com',
            "port"      : 587
        },
        "subject"   : "Your subject",
        "from"      : "your_email@mail.com",
        "to"        : "example@mail.com",
        "text"      : text,
        "html"      : html
    })
