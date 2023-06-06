
<template>
	<div class="map-wrap">
	
	<a href="https://www.maptiler.com" class="watermark"><img
	src="https://api.maptiler.com/resources/logo.svg" alt="MapTiler logo"/></a>
	<div class="map" ref="mapContainer"></div>
	</div>
    <link href="https://unpkg.com/maplibre-gl@3.0.1/dist/maplibre-gl.css" rel="stylesheet" />
  </template>
  
  <script>
  /* eslint-disable */
//   import { Map, NavigationControl, Marker } from 'maplibre-gl';
//   import { shallowRef, onMounted, onUnmounted, markRaw } from 'vue';
	import maplibregl from 'maplibre-gl';
	import 'maplibre-gl/dist/maplibre-gl.css';
  	import {shallowRef, onMounted, onUnmounted } from 'vue';
	import axios from 'axios';
	import Supercluster from 'supercluster';
	// import usersData from "./data.geojson";




  export default {
	

	name: "Map",
	setup () {
	  const mapContainer = shallowRef(null);
	  const map = shallowRef(null);
	  let fddata='';
	  var myGeoJSON = {};

	  const date={
    "type": "FeatureCollection",
    "features": [
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    28.612241934,
                    35.7266807
                ]
            },
            "properties": {
                "id": 1,
                "type": 1
            }
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    23.409070875,
                    34.87859794
                ]
            },
            "properties": {
                "id": 2,
                "type": 2
            }
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    28.216187648,
                    35.762184606
                ]
            },
            "properties": {
                "id": 3,
                "type": 1
            }
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    22.975954174,
                    38.531446571
                ]
            },
            "properties": {
                "id": 4,
                "type": 1
            }
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    22.393816166,
                    36.100487284
                ]
            },
            "properties": {
                "id": 5,
                "type": 1
            }
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    21.226893052,
                    38.863405595
                ]
            },
            "properties": {
                "id": 6,
                "type": 1
            }
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    21.315949512,
                    37.757070254
                ]
            },
            "properties": {
                "id": 7,
                "type": 1
            }
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    28.007233548,
                    36.007053994
                ]
            },
            "properties": {
                "id": 8,
                "type": 1
            }
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    24.990118343,
                    36.977040138
                ]
            },
            "properties": {
                "id": 9,
                "type": 1
            }
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    27.159313179,
                    37.220934158
                ]
            },
            "properties": {
                "id": 10,
                "type": 1
            }
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    26.795632236,
                    36.207111118
                ]
            },
            "properties": {
                "id": 11,
                "type": 1
            }
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    23.599772045,
                    37.875550111
                ]
            },
            "properties": {
                "id": 12,
                "type": 1
            }
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    27.249804435,
                    37.932407955
                ]
            },
            "properties": {
                "id": 13,
                "type": 2
            }
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    20.568802133,
                    37.869848658
                ]
            },
            "properties": {
                "id": 14,
                "type": 1
            }
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    21.269686364,
                    36.315835724
                ]
            },
            "properties": {
                "id": 15,
                "type": 2
            }
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    25.297311099,
                    36.607548422
                ]
            },
            "properties": {
                "id": 16,
                "type": 2
            }
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    23.563816503,
                    39.588233446
                ]
            },
            "properties": {
                "id": 17,
                "type": 1
            }
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    19.943554305,
                    40.449428457
                ]
            },
            "properties": {
                "id": 18,
                "type": 1
            }
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    24.43128476,
                    41.050505005
                ]
            },
            "properties": {
                "id": 19,
                "type": 1
            }
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    23.898386007,
                    35.319825762
                ]
            },
            "properties": {
                "id": 20,
                "type": 1
            }
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    19.15948266,
                    36.452219593
                ]
            },
            "properties": {
                "id": 21,
                "type": 1
            }
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    22.753136997,
                    40.890294257
                ]
            },
            "properties": {
                "id": 22,
                "type": 1
            }
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    22.878160245,
                    38.52323539
                ]
            },
            "properties": {
                "id": 23,
                "type": 1
            }
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    28.57400655,
                    37.961190114
                ]
            },
            "properties": {
                "id": 24,
                "type": 1
            }
		}
		]
	}
	  
	  onMounted(() => {
		const supercluster = new Supercluster({
		radius: 1000, 
		maxZoom: 15 
		});
	    supercluster.load(date.features);
        map.value = new maplibregl.Map({
        container:  mapContainer.value,
        style:
        'https://api.maptiler.com/maps/streets/style.json?key=get_your_own_OpIi9ZULNHzrESv6T2vL',
        center: [12.550343, 55.665957],
        zoom: 8
        });

        map.value.on('load', function () {
       
        const supercluster = new Supercluster({
        radius: 40,
        maxZoom: 16
        });

        supercluster.load(date.features);

        map.value.loadImage("https://jawg.github.io/maplibre-gl-js-examples/icons/cluster/tree-cluster.png", (error, image) => {
        if (error) throw error;
        map.value.addImage("tree-cluster", image);
        });
        map.value.loadImage("https://docs.mapbox.com/mapbox-gl-js/assets/custom_marker.png", (error, image) => {
            if (error) throw error;
            map.value.addImage("custom-icon", image);
        });
      
      
        map.value.addSource('earthquakes', {
                type: 'geojson',
                data: date,
                cluster: true,
                clusterMaxZoom: 14, 
                clusterRadius: 50 
            });
        
        map.value.addLayer({
            id: 'clusters',
            type: 'circle',
            source: 'earthquakes',
            filter: ['has', 'point_count'],
            paint: {
                'circle-color': [
            'step',
            ['get', 'point_count'],
            '#0000FF',
            100,
            '#0000FF',
            750,
            '#0000FF'
            ],

            'circle-radius': 20,
            "circle-stroke-width": 1,
            'circle-stroke-color':'#FFFFFF',
            "circle-opacity-transition": {"duration": 0 , "delay": 0}
        },
        }),
      
      
        map.value.addLayer({
            id: 'cluster-count',
            type: 'symbol',
            source: 'earthquakes',
            filter: ['has', 'point_count'],
            layout: {
                'text-field': '{point_count_abbreviated}',
                'text-font': ['DIN Offc Pro Medium', 'Arial Unic							ode MS Bold'],
                'text-size': 16,
                
            },
            paint: {
            'text-color':'#FFFFFF',
            "text-opacity-transition": {
            "duration": 0,
            "delay": 0
            }
         }
        });
                
        map.value.addLayer({
            id: 'unclustered-point',
            type: 'symbol',
            source: 'earthquakes',
            filter: ['!', ['has', 'point_count']],
            paint: {
              
            },layout:{
            'icon-image': [
            'case',
            ['==', ['get', 'type'], 1],
            'tree-cluster',
             'custom-icon'
            ]
            }
        });
       

        map.value.on('click', 'clusters', function (e) {
            var features = map.queryRenderedFeatures(e.point, {
                layers: ['earthquakes']
            });
            var clusterId = features[0].properties.cluster_id;
            map.getSource('earthquakes').getClusterExpansionZoom(
                clusterId,
                function (err, zoom) {
                    if (err) return;
                    map.easeTo({
                        center: features[0].geometry.coordinates,
                        zoom: zoom
                    });
                }
            );
        });

        map.value.on('click', 'unclustered-point', function (e) {
            var coordinates = e.features[0].geometry.coordinates.slice();
            var mag = e.features[0].properties.mag;
            var tsunami;
            if (e.features[0].properties.tsunami === 1) {
                tsunami = 'yes';
            } else {
                tsunami = 'no';
            }
            // Ensure that if the map is zoomed out such that
            // multiple copies of the feature are visible, the
            // popup appears over the copy being pointed to.
            while (Math.abs(e.lngLat.lng - coordinates[0]) > 180) {
                coordinates[0] += e.lngLat.lng > coordinates[0] ? 360 : -360;
            }
            new maplibregl.Popup()
                .setLngLat(coordinates)
                .setHTML(
                    'magnitude: ' + mag + '<br>Was there a tsunami?: ' + tsunami
                )
                .addTo(map);
        });
        map.value.on('mouseenter', 'clusters', function () {
            map.value.getCanvas().style.cursor = 'pointer';
        });
        map.value.on('mouseleave', 'clusters', function () {
            map.value.getCanvas().style.cursor = '';
        });
    });
	  }),
	 
	  onUnmounted(() => {
		map.value?.remove();
	  })
	  return {
		map,mapContainer
	  };
	}
  };

  </script>
  
  
  <style scoped>
  @import '~maplibre-gl/dist/maplibre-gl.css';

  body { margin: 0; padding: 0; }
  #map { position: absolute; top: 0; bottom: 0; width: 100%; }
  .map-wrap {
	position: relative;
	width: 100%;
	height: calc(100vh - 77px); /* calculate height of the screen minus the heading */
  }
  
  .map {
	position: absolute;
	width: 100%;
	height: 100%;
  }
  
  .watermark {
	position: absolute;
	left: 10px;
	bottom: 10px;
	z-index: 999;
  }
  </style>