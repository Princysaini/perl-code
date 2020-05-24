#!/usr/bin/perl

use strict;
use warnings;

$ARGV[2] or die "use get.pl <File with IDs> <Input Fasta> <Output Fasta>\n";
my $list_file = shift @ARGV;
my $fasta_in = shift @ARGV;
my $fasta_out = shift @ARGV;

my %sel;
open (my $lh, "<", $list_file) or die;
while (<$lh>) {
    chomp;
    $sel{$_}++;
}
close $lh;

$/ = "\n>";
open (my $ih, "<", $fasta_in) or die;
open (my $oh, ">", $fasta_out) or die;
while (<$ih>) {
    s/>//g;
    my ($id_line, @seq) = split (/\n/, $_);
    if ($id_line =~ /gene=(\w+)/) {
        my $id = $1;
        if (defined $sel{$id}) {
            print $oh ">$id\n";
            print $oh join "\n", @seq;
            print $oh "\n";
        }
    }
}
close $ih;
close $oh;
