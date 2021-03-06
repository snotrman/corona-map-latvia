<html>

<head>
    <title>Corona Izplatība Latvijā 24/7</title>
    <meta
        name="viewport"
        content="initial-scale=1.0, user-scalable=no"
    >
    <meta charset="utf-8">
    <style>
        /* Always set the map height explicitly to define the size of the div
           * element that contains the map. */
        #map {
            height: 100%;
        }

        /* Optional: Makes the sample page fill the window. */
        html,
        body {
            height: 100%;
            margin: 0.5em;
            padding: 0.1em;
        }

        .popup-bubble {
            /* Position the bubble centred-above its parent. */
            position: absolute;
            top: 0;
            left: 0;
            transform: translate(-50%, -100%);
            /* Style the bubble. */
            background-color: white;
            padding: 5px;
            border-radius: 5px;
            font-family: sans-serif;
            overflow-y: auto;
            max-height: 60px;
            box-shadow: 0px 2px 10px 1px rgba(0, 0, 0, 0.5);
        }

        /* The parent of the bubble. A zero-height div at the top of the tip. */
        .popup-bubble-anchor {
            /* Position the div a fixed distance above the tip. */
            position: absolute;
            width: 100%;
            bottom:
                /* TIP_HEIGHT= */
                8px;
            left: 0;
        }

        /* This element draws the tip. */
        .popup-bubble-anchor::after {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            /* Center the tip horizontally. */
            transform: translate(-50%, 0);
            /* The tip is a https://css-tricks.com/snippets/css/css-triangle/ */
            width: 0;
            height: 0;
            /* The tip is 8px high, and 12px wide. */
            border-left: 6px solid transparent;
            border-right: 6px solid transparent;
            border-top:
                /* TIP_HEIGHT= */
                8px solid white;
        }

        /* JavaScript will position this div at the bottom of the popup tip. */
        .popup-container {
            cursor: auto;
            height: 0;
            position: absolute;
            /* The max width of the info window. */
            width: 200px;
        }

    </style>
</head>

<body>
    <div id="map"></div>
    <script>
        function initMap() {
            var map = new google.maps.Map(document.getElementById('map'), {
                center: {
                    lat: 56.955533,
                    lng: 24.090859
                },
                zoom: 11,
                styles: [{
                    elementType: "geometry",
                    stylers: [{
                        color: "#1d2c4d"
                    }]
                }, {
                    elementType: "labels.icon",
                    stylers: [{
                        visibility: "off"
                    }]
                }, {
                    elementType: "labels.text",
                    stylers: [{
                        color: "#51bfea"
                    }, {
                        weight: 8
                    }]
                }, {
                    elementType: "labels.text.fill",
                    stylers: [{
                        color: "#0bf0f0"
                    }]
                }, {
                    elementType: "labels.text.stroke",
                    stylers: [{
                        color: "#1a3646"
                    }, {
                        visibility: "off"
                    }]
                }, {
                    featureType: "administrative.land_parcel",
                    elementType: "labels",
                    stylers: [{
                        visibility: "off"
                    }]
                }, {
                    featureType: "administrative.land_parcel",
                    elementType: "labels.text.fill",
                    stylers: [{
                        color: "#64779e"
                    }]
                }, {
                    featureType: "administrative.locality",
                    stylers: [{
                        weight: 8
                    }]
                }, {
                    featureType: "administrative.province",
                    stylers: [{
                        visibility: "off"
                    }]
                }, {
                    featureType: "administrative.province",
                    elementType: "geometry.stroke",
                    stylers: [{
                        color: "#4b6878"
                    }]
                }, {
                    featureType: "landscape",
                    stylers: [{
                        color: "#f50530"
                    }, {
                        weight: 8
                    }]
                }, {
                    featureType: "landscape.man_made",
                    elementType: "geometry.stroke",
                    stylers: [{
                        color: "#334e87"
                    }]
                }, {
                    featureType: "landscape.natural",
                    elementType: "geometry",
                    stylers: [{
                        color: "#5a617e"
                    }]
                }, {
                    featureType: "poi",
                    stylers: [{
                        visibility: "off"
                    }]
                }, {
                    featureType: "poi",
                    elementType: "geometry",
                    stylers: [{
                        color: "#283d6a"
                    }]
                }, {
                    featureType: "poi",
                    elementType: "labels.text",
                    stylers: [{
                        visibility: "off"
                    }]
                }, {
                    featureType: "poi",
                    elementType: "labels.text.fill",
                    stylers: [{
                        color: "#6f9ba5"
                    }]
                }, {
                    featureType: "poi",
                    elementType: "labels.text.stroke",
                    stylers: [{
                        color: "#1d2c4d"
                    }]
                }, {
                    featureType: "poi.government",
                    stylers: [{
                        color: "#ffeb3b"
                    }]
                }, {
                    featureType: "poi.park",
                    elementType: "geometry.fill",
                    stylers: [{
                        color: "#023e58"
                    }]
                }, {
                    featureType: "poi.park",
                    elementType: "labels.text.fill",
                    stylers: [{
                        color: "#3C7680"
                    }]
                }, {
                    featureType: "road",
                    elementType: "geometry.fill",
                    stylers: [{
                        color: "#f50530"
                    }]
                }, {
                    featureType: "road",
                    elementType: "labels.text.fill",
                    stylers: [{
                        color: "#98a5be"
                    }]
                }, {
                    featureType: "road",
                    elementType: "labels.text.stroke",
                    stylers: [{
                        color: "#1d2c4d"
                    }]
                }, {
                    featureType: "road.highway",
                    stylers: [{
                        color: "#f94262"
                    }]
                }, {
                    featureType: "road.highway",
                    elementType: "geometry",
                    stylers: [{
                        color: "#f50530"
                    }, {
                        visibility: "on"
                    }, {
                        weight: 2.5
                    }]
                }, {
                    featureType: "road.highway",
                    elementType: "geometry.fill",
                    stylers: [{
                        color: "#f50530"
                    }, {
                        visibility: "on"
                    }]
                }, {
                    featureType: "road.highway",
                    elementType: "geometry.stroke",
                    stylers: [{
                        color: "#6f708e"
                    }, {
                        weight: 0.5
                    }]
                }, {
                    featureType: "road.highway",
                    elementType: "labels.text.fill",
                    stylers: [{
                        color: "#b0d5ce"
                    }]
                }, {
                    featureType: "road.highway",
                    elementType: "labels.text.stroke",
                    stylers: [{
                        color: "#023e58"
                    }]
                }, {
                    featureType: "road.local",
                    elementType: "labels",
                    stylers: [{
                        visibility: "off"
                    }]
                }, {
                    featureType: "transit",
                    stylers: [{
                        visibility: "on"
                    }]
                }, {
                    featureType: "transit",
                    elementType: "labels.text.stroke",
                    stylers: [{
                        color: "#1d2c4d"
                    }]
                }, {
                    featureType: "transit.line",
                    elementType: "geometry.fill",
                    stylers: [{
                        color: "#f50530"
                    }, ]
                }, {
                    featureType: "transit.station",
                    elementType: "geometry",
                    stylers: [{
                        color: "#3a4762"
                    }]
                }, {
                    featureType: "water",
                    stylers: [{
                        color: "#fe3d63"
                    }]
                }, {
                    featureType: "water",
                    elementType: "labels.text.fill",
                    stylers: [{
                        color: "#4e6d70"
                    }]
                }, {
                    featureType: 'water',
                    elementType: 'geometry',
                    stylers: [{
                        color: '#17263c'
                    }]
                }, ]
            });
            var rixCoord = {
                lat: 56.924875,
                lng: 23.976440
            }
            var rigaCoord = {
                lat: 56.949172,
                lng: 24.096453
            }
            var rigaIcon = {
                url: "https://iconsplace.com/wp-content/uploads/_icons/fffff0/256/png/biohazard-icon-7-256.png",
                size: new google.maps.Size(71, 71),
                origin: new google.maps.Point(0, 0),
                anchor: new google.maps.Point(17, 34),
                scaledSize: new google.maps.Size(50, 50)
            };
            var rixIcon = {
                url: "https://iconsplace.com/wp-content/uploads/_icons/fffff0/256/png/biohazard-icon-7-256.png",
                size: new google.maps.Size(71, 71),
                origin: new google.maps.Point(0, 0),
                anchor: new google.maps.Point(17, 34),
                scaledSize: new google.maps.Size(25, 25)
            }
            var rigaMarker = addMarker(rigaCoord, map, rigaIcon, "10", "<h2>Kopā Latijā ir: 10 saslimušo, 12.03.20</h2> <a>https://twitter.com/SPKCentrs?ref_src=twsrc%5Egoogle%7Ctwcamp%5Eserp%7Ctwgr%5Eauthor</a>");
            var rixMarker = addMarker(rixCoord, map, rixIcon, "LV:10", "</div>no kuriem viena sievieta atlidoja no Milānas un 9 cilvēki no Ziemeļitālijas <a>https://www.tvnet.lv/6919673/latvija-apstiprinati-10-saslimsanas-gadijumi-ar-covid-19</a></div>");
            var lineCoordinates = [
                rixCoord,
                rigaCoord,
            ];
            var linePath = new google.maps.Polyline({
                path: lineCoordinates,
                geodesic: true,
                strokeColor: '#ffffff'
            });
            linePath.setMap(map);

        }

        function addMarker(coordinates, map, icon, labelText, description) {
            // Add the marker at the clicked coordinates, and add the next-available label
            // from the array of alphabetical characters.
            var marker = new google.maps.Marker({
                position: coordinates,
                label: {
                    color: '#FFFFFF', // <= HERE
                    fontSize: '1.5em',
                    fontWeight: '900',
                    text: labelText
                },
                icon: icon,
                map
            });

            var infowindow = new google.maps.InfoWindow({
                content: description
            });

            marker.addListener('click', function () {
                infowindow.open(map, marker);
            });
        }

    </script>
    <script
        src="https://maps.googleapis.com/maps/api/js?key=AIzaSyDDZeOR-Rftpjab_ogG2DdmDEiLns-_XC4&callback=initMap"
        async
        defer
    ></script>
</body>
</body>

</html>
