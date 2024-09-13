 # (Assuming Django framework)

from django.db import models

class Match(models.Model):
    home_team = models.ForeignKey('Team', on_delete=models.CASCADE, related_name='home_matches')
    away_team = models.ForeignKey('Team', on_delete=models.CASCADE, related_name='away_matches')
    date = models.DateField()
    score = models.CharField(max_length=20)
    screenshot = models.URLField(blank=True, null=True)  # Store screenshot URL

class Player(models.Model):
    name = models.CharField(max_length=100)
    email = models.EmailField()
    password = models.CharField(max_length=128)
    team = models.ForeignKey('Team', on_delete=models.SET_NULL, null=True)

class Team(models.Model):
    name = models.CharField(max_length=100)

class Tournament(models.Model):
    name = models.CharField(max_length=100)
    type = models.CharField(max_length=50)  # (e.g., "double round-robin", "knockout")
    
