# Eventmaker.io Templates Sample 

Fichiers templates des sites sont présents dans /mobicheckin/website/standard/

Notre système de theming sur la base de :

A/ Un fichier de layout principal (/mobicheckin/website/standard/layouts/theme.liquid)
B/ Des fichiers de sections (/mobicheckin/website/standard/sections/*.liquid)

----------------------------------------------------

Le language de templating utilisé est "Liquid" developpé par Shopify, 
une doc est disponible ici : https://shopify.github.io/liquid/

Tour rapide du language Liquid 

Opérateurs
`==` égalité
`!=` non égalité

Condition simple
`{% if condition == true %} It's true {% endif%}`

Condition avancé
`{% if condition == true %} It's true {% elsif condition == false %} It's false {% else %} It's not true nor false {% endif%}`

Affichage d'une variable
`{{ ma_var }}`

Commentaire 
`{% comment %} Ceci est un commentaire {% endcomment %}`

----------------------------------------------------

A/ Theme.liquid
Ce fichier contient le corps du template avec les tags html génériques: Html, Head et Body.
Comme dans tout fichier html, il est possible de faire appels à des ressources internes (inline) ou distantes hébergées sur serveur https (Github/ Aws / Ovh ou n'importe quel serveur https)

B/ Les sections ou modules
Elles se composent de deux parties :

- Une partie gérant l'affichage et le balisage des données

- Une partie de définition des paramètres de champs de la section en Json :

    `{% schema %}
        {
            "name": "Title only",
            "name_translations": { "fr": "Titre seul" },
            "class": "index-section",
            "icon": "fa fa-font",
            "hidden_from_user": false,
            "settings": [
                    {
                        "type": "text",
                        "id": "title",
                        "label": "Title",
                        "label_translations": { "fr": "Titre" },
                        "default": "Title",
                        "default_translations": { "fr": "Titre" }
                    },
                    ...
                            {
                                "label": "Left",
                                "label_translations": { "fr": "Gauche" },
                                "value": "left"
                            }
                        ]
                    }
                ],
                "presets": [
                {
                    "name": "Title only",
                    "name_translations": { "fr": "Titre seul" }
                }
            ]
        }
    {% endschema %}`

----------------------------------------------------

Le chargement du template s'effectue depuis l'interface Website d'Eventmaker, à partir de l'icône reload [Capture]

Ce dernier peut s'effectuer directement depuis un serveur local avec accès extérieur ex Serveo.net / Ngrok ou tout autre système de tunneling (1).

Ou directement depuis un Git héberger 
ex. : laurent.github.net (2)

Pré-requis : l'adresse dans le champs reload doit être le point d'entrée du repo sans modifier l'arborescences.

Un serveur http en local (Apache/NodeJS/etc..)

App Tunneling - Chargement local <> externe
NodeJs
https://localtunnel.github.io/www/ 
https://ngrok.com/

----------------------------------------------------

FAQ
Peut-on ajouter des images ou des ressources et les utiliser directement dans le repo ?
Les liens des ressources doivent être renseignées en absolue.
Ex: https://mondomain.com/img.jpg
A ne pas faire: ../img.jpg

Do / Dont

----------------------------------------------------

