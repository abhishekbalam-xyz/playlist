<!DOCTYPE html>
<html lang="en">

{% include head.md %}

<body>
	<div class="limiter">
		<div class="container-table100">
			<div class="wrap-table100">
				<h1 style="text-align: center;color: #FFF" class="table"> Playlist of songs that I think you'll like</h1>
				<h5  style="text-align: center;color: #FFF" class="table">A list of awesome songs that I'm listening to these days..</h5>
				<h4 style="text-align: center;color: #FFF" class="table">[Last Updated: {{ page.date | date: "%B, %Y"}}]</h4>
				<div class="table100">
					<h3 style="padding-top:20px;text-align: center;" class="table"><a href="player/" style="color: #FEF" ><i class="ion-play" style="font-size: 4rem"></i><br>Play</a></h3>
					<table>
						<thead>
							<tr class="table100-head">
								<th class="column1">Song</th>
								<th class="column2">Audio</th>
								<th class="column3">Download</th>
							</tr>
						</thead>
						<tbody>							
							{% assign music_files = site.static_files | where: "music", true %}							
							{% for track in music_files %}
								{% if track.extname contains ".mp3" %}
						  		<tr>
									<td class="column1" style="text-transform: capitalize;">{{ track.basename | replace: "_"," 	"}}</td>
									<td class="column2">
										<audio controls>
  											<source src="{{ track.path }}" type="audio/mpeg">
  										</audio>
									</td>
									<td class="column3">
										<a href="{{ track.path }}" download>
											Download: &nbsp;
											<i class="fa fa-download" aria-hidden="true"></i>
										</a>
									</td>
								</tr>
								{% elsif track.extname contains ".zip" %}
									{% assign all_files = track.path %}
								{% endif %}
							{% endfor %}							
						</tbody>
					</table>
					<h3 style="padding-top:20px;text-align: center;" class="table"><a href="{{ all_files }}" style="color: #FEF" download>Download All Songs</a></h3>
				</div>
			</div>
		</div>
	</div>

{% include scripts.md %}

</body>
</html>