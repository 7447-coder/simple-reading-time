<?php
/*
Plugin Name: Simple Reading Time
Description: Shows estimated reading time for blog posts.
Version: 1.0
Author: Sakshi Deshmukh
*/

function srt_display_reading_time($content) {
    if (is_single()) {
        $word_count = str_word_count(strip_tags($content));
        $reading_time = ceil($word_count / 200); // 200 words/minute
        $reading_time_html = "<p><strong>Estimated Reading Time: {$reading_time} min read</strong></p>";
        return $reading_time_html . $content;
    }
    return $content;
}

add_filter('the_content', 'srt_display_reading_time');
